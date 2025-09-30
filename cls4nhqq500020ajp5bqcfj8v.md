---
title: "Introduction to HyperLogLog"
seoTitle: "Introduction to probabilistic data structure HyperLogLog"
seoDescription: "Introduction to probabilistic data structure HyperLogLog for counting the distinct number of items in a collection."
datePublished: Fri Feb 02 2024 12:57:55 GMT+0000 (Coordinated Universal Time)
cuid: cls4nhqq500020ajp5bqcfj8v
slug: introduction-to-hyperloglog
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1759229179232/f0bbdbd9-65d8-4719-8726-8d68c721c494.png
tags: data-structures, probabilistic-data-structure, hyperloglog

---

Calculating the *exact* number of distinct items in a collection can be a difficult task if the collection is very large or if you have a very limited amount of memory. Typical approaches can be:

* using a hash map (uses more memory)
    
* using a bit map (uses less memory)
    

but they both need an amount of memory proportional to the cardinality of the collection.

Another approach is using a probabilistic data structure, a type of data structure that doesn't return an exact result but an approximation of that, in favor of memory/CPU savings.

HyperLogLog (HLL from now on) is one of those probabilistic data structures.

### Main intuition

Let's delve into the main intuition behind HLL. Imagine you have a big set of random numbers; if you think about their binary representation, you can safely assume that roughly half of these numbers will start with a "0" and the other half will start with a "1". In the same way, you can assume that roughly one fourth of these numbers will start with "00", another fourth will start with "01", another fourth will start with "10" and the last fourth will start with "11".

Continuing in this direction, we can also safely assume that roughly one-eighth of these numbers will start with a "000", another eighth will start with "001", and so on with the other three-bit combinations.

To generalize, we can say that:

$$p(k \text{ bits})=2^{-k}$$

that we can read as the probability of having specific *k* leading bits is equals to two to the -*k*.

With this idea in mind, let's see how it connects to computing the number of distinct items of a collection. Let's imagine we have a set with a lot of objects: if we apply to them a [hash function](https://en.wikipedia.org/wiki/Hash_function), we transform this set of objects into a set of numbers (so, exactly as the set we saw in the intuition example).

Suppose we add a new object to the set: we apply the hash function to it and we get a number; if for example the binary representation of this number starts with "000" we can say that it's likely that the set has a size of 2^3, where the 3 is the number of 0s we have in "000" (as we saw in the intuition example, one eighth of the numbers will have three leading 0s and so we can say that the set is likely to be of size 8). If the binary representation of the number started with "0000", then we could have said that the set is likely to have 16 items (16 = 2^4, where 4 is the number of leading 0s), because only one sixteenth of the items will start with 4 leading 0s.

**Caveats**

There are two very big caveats in order for this intuition to work properly:

* the set must have a lot of items
    
* the hash function used for transforming the object into a number must return uniformly distributed binary representations
    

Of course, there's the risk that one outlier breaks this logic: what if the first element we insert has a binary representation of "0000000000000011"? In this case the estimated size of the set would be 2^14 (16,384) which is blatantly wrong. To avoid this issue, HLL uses multiple (virtual) hash functions, so that if one of them returns an outlier, it will be compensated by the others (we'll see in a later paragraph why I called them virtual).

### Data Structure details

Now that the main idea is clear, let's get into the details of the data structure. HLL is composed of:

* a hash function
    
* an array of number, called *M*
    

HLL uses a clever trick to save CPU time for computing the hash and, in order to understand how it works, let's first imagine we have 16 hash functions and an array of numbers *M* of size 16 (the same value as the number of hash functions).

When we insert an item X, we apply the first hash function to X and we write the number of leading 0s of the binary representation of the returned number in the first position of the array. Then we apply the second hash function to X and we write the value obtained in the second position of the array, and so on for the third hash function, the fourth, up to the sixteenth.

So let's say the hash functions return these values:

$$\displaylines{ h_1(x) = 0000100100101001 \\ h_2(x) = 0011100110011010 \\ h_3(x) = 0101011110100011 \\ h_4(x) = 1111100111101001 \\ ... \\ h_{16}(x) = 0001100001001100 }$$

We insert the number of leading 0s of these numbers and the array *M* will be:

```plaintext
4 | 2 | 1 | 0 | 2 | 1 | 2 | 1 | 3 | 0 | 2 | 1 | 3 | 0 | 1 | 3
```

Then we insert a second object, Y. We again apply the sixteen hash functions, and if the value of leading 0s of any of them is greater than the value found in the corresponding position in the array, we replace the value.

So let's say the hash functions return these values:

$$\displaylines{ h_1(y) = 0011001000101000 \\ h_2(y) = 1011100110011010 \\ h_3(y) = 0011010010101111 \\ h_4(y) = 0001100001111001 \\ ... \\ h_{16}(y) = 0010011011000101 }$$

We insert the number of leading 0s of these number and the array *M* will be:

```plaintext
4 | 2 | 2 | 3 | 2 | 1 | 3 | 1 | 3 | 0 | 3 | 2 | 3 | 0 | 2 | 3
```

please note that only values at indexes 2, 3, 6, 10, 11 and 14 have changed, and the changed values are all greater than they were before.

So the more we insert items into the HLL data structure, the more the values of the array will get higher.

### Using only one hash function

The clever approach of HLL to save CPU time is pretending it computes multiple hash functions, while in reality it only computes one. Let's see how.

The value returned by the only hash function is divided into two sets of bits: the first *n* and the remaining *m.* Let's make a practical example: let's say the hash function return a 32 bit integer, we set *n* to be 4 and *m* to be the remaining 28.

```plaintext
h(x) = 1 1 0 0 0 1 1 1 0 0 1 1 0 1 1 1 0 1 0 0 0 0 1 1 0 1 1 1 0 1 1 0 
       ------- -------------------------------------------------------
          |                              | 
       4 bits                         28 bits
```

The first *n* bits (in our example 4 bits) are used calculate the index in the *M* array and the remaining *m* bits are used for the value.

Let's see it in practice. When we insert a new item X, we apply the hash function that returns a number whose binary representation is 11000111001101110100001101110110; the first 4 bits are 1100, which is 12 in decimal, so the index where we will write is 12. The remaining 28 bits (0111001101110100001101110110) have only one leading 0, so the value we write at index 12 is 1. After inserting X, the *M* array will be:

```plaintext
0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0
```

Now we insert Y, and the hash function applied to Y returns a number whose binary representation is 00110000101011000110111000100101. The first 4 bits are 0011 (which 3 in decimal) and the remaining 28 bits are 0000101011000110111000100101 which has 4 leading zeros. So we will write 4 at index 3 of the array:

```plaintext
0 | 0 | 0 | 4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0
```

As we keep inserting new values into the array, we'll get the array filled up with values, exactly as when we used 16 hash functions, the only difference being that with only one hash function the array *M* fills/updates at a sixteenth of the speed of the initial example where we had 16 hash functions.

### Estimating the cardinality

Now that we understood how the hash function and the array *M* work, we can get to the computation of the estimate cardinality, which uses the harmonic mean of the values of the array *M* (expressed as *Z* in the formula), the size of the array *M* (expressed as *m* in the formula) and a correction factor ⍺. The formula is:

$$\text{cardinality} = Z \cdot m^2 \cdot \alpha$$

where

<iframe src="https://math.embed.fun/embed/fsbM4m5NQJ4p2bcjz9SiWs" width="200" height="169"></iframe>

and

<iframe src="https://math.embed.fun/embed/wmv7AjaSDY9JWaDBZ15QEr" width="223" height="228"></iframe>

Let's compute an example. Let's say our array *M* has size 16, and its values are:

```plaintext
4 | 5 | 2 | 3 | 5 | 4 | 7 | 2 | 6 | 5 | 4 | 5 | 3 | 6 | 2 | 5
```

then the cardinality will be given by:

$$\text{cardinality} = Z \cdot m^2 \cdot \alpha \approx 0.72 \cdot 256 \cdot 0.673 \approx 124.59$$

Let's see how HLL deals with outliers. Let's change the third value of the array *M* to 12 (which - taken alone - should give a 2,048 estimated size):

```plaintext
4 | 5 | 12 | 3 | 5 | 4 | 7 | 2 | 6 | 5 | 4 | 5 | 3 | 6 | 2 | 5
```

if we compute the cardinality given these values of *M*, we get:

$$\text{cardinality} = Z \cdot m^2 \cdot \alpha \approx 0.88 \cdot 256 \cdot 0.673 \approx 152.06$$

As you can see, there's no big difference between the 124.59 we got before the change and the 152.06 we got after the change, thanks to the fact that the harmonic mean of the *M* values is changing only from 0.72 to 0.88, leveling down the value of the outlier.

### References

The original paper was published in 2007 by Flajolet *et al*, and you can find it at [https://algo.inria.fr/flajolet/Publications/FlFuGaMe07.pdf](https://algo.inria.fr/flajolet/Publications/FlFuGaMe07.pdf) .