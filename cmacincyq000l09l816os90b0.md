---
title: "Cognitive Science based Software Engineering"
seoTitle: "Cognitive Science in Software Engineering"
seoDescription: "Optimize software engineering with cognitive science: enhance code comprehension, memory use, and reduce cognitive load"
datePublished: Tue May 06 2025 12:59:10 GMT+0000 (Coordinated Universal Time)
cuid: cmacincyq000l09l816os90b0
slug: cognitive-science-based-software-engineering
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1746536282301/e864cded-8fe8-4dc5-87db-c6b6f057d0b2.png
tags: software-development, software-engineering, cognitive-science

---

Have you ever wondered why some code is easier to understand than others? Or why you can remember complex notions like design patterns or algorithms but struggle to recall an arbitrary sequence of numbers? The answers lie in cognitive science, the interdisciplinary study of the mind and its processes.

As software engineers, our primary tool isn't our computer, it's our brain. We usually obsess over optimizing our code, but we rarely consider optimizing how our minds interact with that code: this article explores how understanding cognitive science can transform our approach to software engineering. For the better.

# Memory

Memory is the cornerstone of human cognition: it shapes how we process information, solve problems, and learn new skills. For software engineers, understanding the memory system is crucial because programming involves constantly dealing with multiple concepts simultaneously.

Our brain's memory isn't a uniform storage system. Instead, it consists of multiple specialized systems working in concert, each with different capacities, duration, and purposes; they are:

* Short Term Memory
    
* Working Memory
    
* Long Term Memory
    

## Short Term Memory

Short term memory is the memory that comes into play when, for example, you want to remember a sequence of numbers. In 1956 G.A. Miller wrote the paper “[The magical number seven, plus or minus two](https://psycnet.apa.org/record/1957-02914-001)”, where he stated that the number of items a person can store in their short term memory is on average seven items (plus or minus two). More recently (2001) the article “[The magical number 4 in short-term memory](https://pubmed.ncbi.nlm.nih.gov/11515286/)” by N. Cowan states that the average number of items is four (plus or minus one). Even more recent studies state that the number varies according to the category of the items; all those numbers are different, but there’s one thing all these studies agree on: **the number of items that can be stored in short term memory is limited.**

Other studies take into account the duration of short term memory, which is estimated to be between 15 and 30 seconds: after that amount of time, the content of the short term memory is gone. Association and rehearsal consolidate information to long term memory, where it can last a lot longer.

Let’s see how it works in practice: try to memorize this sequence of numbers:

$$9\qquad5\qquad 8\qquad 6\qquad 5\qquad 5\qquad 3\qquad 6$$

Sometime it’s easier to remember if divided in chunks:

$$9\qquad5\qquad 8\qquad 6\qquad \qquad \quad 5\qquad 5\qquad 3\qquad 6$$

Later I’ll ask you if you can remember those numbers, try to memorize them.

## Working Memory (WM)

Working memory is very close to short term memory, some researches even use the two terms interchangeably. We can define the working memory as short term memory applied to processing some task.

Let’s make an example: how much is 16 × 9 ?

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Before going on reading, try to compute the result of this multiplication in your mind.</strong></div>
</div>

If you did like me, you multiplied 9 by 10 and then summed to it the result of multiplying 9 by 6. In numbers: 9 x 10 + 9 × 6, which is 90 + 54, that is 144. Another way of doing it is multiply 16 by 10 and subtract 16, and the result will obviously be the same.

You probably did it without any particular issue, so I would like you to try to compute in your mind another one:

how much is 23 × 68 ?

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Before going on reading, try to compute the result of this multiplication in your mind.</strong></div>
</div>

I don’t know you, but I struggled with this one. My idea was to compute 68 × 20 and then summing 68 × 3; first I computed 68 x 20, which is easy because is the double of 68 × 10, which is 680, so it’s 1,360. Then I computed 68 × 3, which is in turn 60 × 3 + 8 × 3, which 180 + 24, in total 204. At this point I had already forgotten the initial 1,360 that I needed to add in order to find the final result. The second time I tried, I succeeded, because I did the same computation, and - as stated before - repetition helps in consolidating values.

If you struggled like I did, what you experienced is having hit the short term memory capacity limit: you had the result of the first multiplication (1,360) in the short term memory and when you computed 180 and 24, those intermediate values took the place of 1,360 making it not available anymore.

## Long Term Memory

When we rehearse or find associations for items in short term memory, we consolidate that information from short term memory to long term memory, where it will be stored for a lot more time; actually, if we retrieve that information frequently, it will be stored for our whole life.

We have three types of long term memory:

* Procedural or Implicit
    
* Declarative or Explicit, which can be of two types:
    
    * Episodic
        
    * Semantic
        

### Procedural or Implicit

This is the kind of memory that allows us to do something without thinking about it, like when riding a bicycle or driving a car while thinking to something else: once learned, there’s no need to think what movements to do in order to go, the body *knows* it and does it without conscious control. A long time [vi](https://en.wikipedia.org/wiki/Vi_\(text_editor\)) user, for example, doesn’t need to tell the fingers where to move to hit the the keys for the sequence `ESC : q !` when they want to discard the changes and close the file: their fingers will press those keys without the user being really conscious about it. The same goes for touch typing and other operations that rely upon the so called *muscle memory*.

### Episodic

This is the kind of memory of what we experienced in first person, like the time we cracked a coding interview or that unfortunate time we broke something in production.

### Semantic

The semantic long term memory is related to learned notions. In software engineering it could be the knowledge of the internals of a data structure like a linked list, or an algorithm like binary search or a design pattern like the Singleton.

# Chunking

In their famous study “[Perception in Chess](https://www.sciencedirect.com/science/article/abs/pii/0010028573900042)”, Chase and Simon showed the difference among beginner, expert and master chess players in recalling the position of pieces on a chessboard. Chess Masters performed exceptionally (recalling around 90%) when reconstructing positions from actual chess games, outperforming both expert players (70%) and beginners (40%). However, this expertise advantage disappeared entirely when the players were presented with random piece configurations, where all skill levels performed comparably poorly (30% accuracy).

These results proved that chess expertise is not based on superior memory capacity, but rather in the ability to recognize and encode meaningful patterns or "chunks" of pieces stored in long term memory derived from extensive playing experience.

Chunking is pervasive in software engineering: when we discuss with a colleague if introducing a Factory into our code, we’re both referring to a common knowledge that we don’t need to explain directly because we both studied the most common software design patterns. The same goes - for example - for python’s list comprehensions, CI/CD pipelines, Rust’s ownership model, microservices architecture, load balancers, message queues and so on.

---

### Quiz

Do you remember the sequence of numbers I asked to memorize?

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">take some time to try to recall it before going on reading!</div>
</div>

If you recalled all the digits, congratulations, you have an outstanding memory! If you didn’t - like me the first time I tried - then you just hit your short term memory duration limit!

The sequence was

$$9\qquad5\qquad 8\qquad 6\qquad 5\qquad 5\qquad 3\qquad 6$$

and here’s a hint for remembering it: think that the men’s world record for running a100 meters is 9.58” and 65,536 is the maximum size of a word (2 bytes, so 2^16): these two numbers contain exactly the same digits as the number I asked you to remember.

With this suggestion the number is a lot easier to recall because instead of remembering a series of 8 digits (which is likely to overflow the capacity limit of short term memory), you just need to remember 2 things: the men 100 meters world record (which might be stored in your long term memory) and 2^16 which again might be stored in your long term memory, especially if you worked with assembly.

---

# Cognitive Load

Cognitive load measures the amount of mental processing required for performing a task. The higher the cognitive load, the higher the fatigue for the brain and the chance of making mistakes when executing a task.

There are three types of cognitive load:

* Intrinsic
    
* Extraneous
    
* Germane
    

## Intrinsic Cognitive Load

Let’s use some code to show what is intrinsic cognitive load. Analyze this function for computing the absolute value of a number:

```java
int abs(int a) {

	if (a < 0) {
		return -a;
	}
		
   return a;
}
```

It’s very simple, it just checks if the number is lesser than zero, and in that case it will return its opposite (thus a positive number) otherwise it will return the positive number given as an input.

Let’s now analyze this function for computing the greatest common divisor:

```java
int gcd(int a, int b) {

	if (b == 0) {
		return a;
	}
		
   return gcd(b, a % b);
}
```

This time, though the code has the same number of lines and the same structure, understanding how it works is more complex because the code is recursive and we have to know some properties of the integer numbers in order to understand why the algorithm works. Probably you did a couple of test runs in your mind, passing some parameter and computing all the recursive calls to make sure it gave the expected result.

The implicit cognitive load of the two algorithms is very different: low for the `abs` function and high for the `gcd`, and the reason is that the second algorithm is intrinsically more difficult to understand and so it creates a higher cognitive load on the brain compared to the first one.

## Extraneous Cognitive Load

Let’s use again some code to explain what extraneous cognitive load is:

```java
 int binSearch(int[]arr, int x) {int 
   l=0; int r=arr.length -1; while    
     (l<=r) {int mid=l+(r-l) /2;
       if(arr[mid]==x){return
        mid;}if(arr[mid]>x) 
         {r=mid-1;}else{
           l= mid+1;}
            return
	          -1 ;
		        }
```

Could you tell if there’s an error in this binary search implementation?

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Take some time to analyze the code and check if it’s correct</div>
</div>

Now check this code:

```java
int binSearch(int[] arr, int x)	{
	int l = 0;
	int r = arr.length - 1;

	while (l <= r) {
		int mid = l + (r - l) / 2;
		if (arr[mid] == x) {
			return mid;
		}

		if (arr[mid] > x) {
			r = mid - 1;
		} else {
			l = mid + 1;
		}
	
	return -1;
}
```

It’s exactly the same code we saw before but, being formatted normally, the missing closing curly brace at the end of the while loop is immediately visible.

Arranging the code in the form of a triangle increases the extraneous cognitive load for understanding the code: it wasn’t the binary search itself difficult to analyze, it was the way the code was formatted that made it more difficult.

## Germane Cognitive Load

Germane cognitive load refers to the mental effort devoted to processing, constructing, and automating schemas that contribute to meaningful learning and skill development. In software engineering, this is the cognitive effort spent on understanding core programming concepts, architectural patterns, or algorithm design principles that build lasting expertise. Unlike extraneous cognitive load or intrinsic cognitive load, germane cognitive load is desirable as it helps engineers convert working experiences into long-term knowledge structures.

---

### Quiz

Do you remember the sequence of numbers I asked to memorize?

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Try to recall the number before going on reading!</div>
</div>

The sequence was

$$9\qquad5\qquad 8\qquad \qquad 6\qquad 5\qquad 5\qquad 3\qquad 6$$

If you recalled it via the athletic world record and the power of two, congratulations: you just leveraged chunking with a new information.

---

# Reading Code

According to [Xin Xia et al,](https://www.researchgate.net/publication/318811113_Measuring_Program_Comprehension_A_Large-Scale_Field_Study_with_Professionals) we developers spend 58% of our time reading code rather than writing it, so let’s get a bit deeper into it. Nowadays with coding agents, it’s even more than 58%, because you read the code that AI writes, don’t you?

Let’s get back to reading code. This is a simple code for computing the length of the longest substring of non-repeating characters in a string:

```java
public int lengthOfLongestSubstring(String s) {
    Set<Character> set = new HashSet<>();
    int n = s.length();
    int maxLength = 0;
    int left = 0;

    for (int right = 0; right < n; right++) {
		while (set.contains(s.charAt(right))) {
			set.remove(s.charAt(left));
			left++;
		}
		set.add(s.charAt(right));
		maxLength = Math.max(maxLength, right - left + 1);
	}

	return maxLength;
}
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Take some time to analyze this code and understand how it computes the length</div>
</div>

When reading code, experienced developers don't just see individual lines—they recognize the roles different variables play. Research by [J. Sajaniemi et al](https://ppig.org/files/2005-PPIG-17th-sajaniemi.pdf) identified common "roles of variables" that help in comprehension:

| **Role (v 2.0)** | **Informal definition** |
| --- | --- |
| Fixed value | A data item that does not get a new proper value after its initialization |
| Stepper | A data item stepping through a systematic, predictable succession of values |
| Most-recent holder | A data item holding the latest value encountered in going through a succession of unpredictable values, or simply the latest value obtained as input |
| Most-wanted holder | A data item holding the best or otherwise most appropriate value encountered so far |
| Gatherer | A data item accumulating the effect of individual values |
| Follower | A data item that gets its new value always from the old value of some other data item |
| One-way flag | A two-valued data item that cannot get its initial value once the value has been changed |
| Temporary | A data item holding some value for a very short time only |
| Organizer | A data structure storing elements that can be rearranged |
| Container | A data structure storing elements that can be added and removed |
| Walker | A data item traversing in a data structure |

Thinking about the snippet we saw before, the main idea is that we use a Set to store the characters we already saw in the string, and then we use two pointers for enlarging/shrinking the subset we’re examining at every step. According to the roles defined above, we can see that:

* `set` is a **Container** that stores characters
    
* `n` is a **Fixed value** representing the length of the input string
    
* `left` is a **Stepper** that used for marking the beginning of the substring
    
* `right` is a **Stepper** that used for marking the end of the substring
    
* `maxLength` is a **Most-wanted holder** keeping track of the best value found (the length of the longest substring)
    

Recognizing these patterns in code helps us create a mental model of the algorithm, allowing us to reason about (among the other things):

* Edge cases
    
* Expected behaviour
    
* Memory consumption
    

Let's look at another example:

```java
public class MovingAverageCalculator {
    private int count = 0;
    private double average = 0.0;
    private double sum = 0.0;

    public void add(double number) {
        sum += number;        
        count++;              
        average = sum / count; 
    }

    public double getAverage() {
        return average;
    }
}
```

This class, as the name clearly suggests, is used for computing the moving average of the numbers added to it. The code is quite straightforward, and it’s actually correct, computing the correct average of the input data.

Now, imagine that an instance of this class is accessed by multiple threads. Oh boy, suddenly, what seemed perfectly legit code, became crap. In a multi-threaded execution, the not synchronized `add` method will just update incorrectly the `average` variable when accessed concurrently by multiple threads.

What we thought was good code one minute ago, became terribly wrong. But the code didn’t change: what changed then? What changed was the way we looked at it, or the **mental model** we used for analyzing it.

## Mental Models

Mental models are crucial for us developers for reasoning about the code we deal with on a daily basis, and come in various forms:

* Algorithm models
    
* System architecture models
    
* Domain models
    

We should always have in mind the mental model of the code/system we’re working on, but we should also not be bounded too much by them. Let’s make an example; these are the Tennis rules:

* Points: 0, 15, 30, 40, Game
    
* To win a game: Score 4 points and be 2 points ahead
    
* To win a set: Win at least 6 games, leading by 2
    
* To win the match: Win 3 out of 5 sets
    

Given an array of the scored points in a tennis match `[p1, p1, p2, p1, ...]` (where the first two points are scored by player 1, the third point by player2, the fourth by player1, and so on), how can we find the winner? With the solid mental model based on the rules listed above, we can loop over the array and update a data structure/class representing games and sets for finding the winner.

But if we can detach from the mental model and reason about what we were asked to find (the winner of the match), it’s incredibly easier just to realize that the player who wins a tennis match is the player who scores the last point: we just need to check the last element of the array to find the winner.

This example was given for highlighting that there are cases in which relying too much on mental models is not always the best approach and in this case with a high extraneous cognitive load, because we introduced unnecessary complexity to something that was simple. This example also highlights the value of diverse teams: different people, especially with different backgrounds, bring with them different mental models or way of approaching problems that can help in finding new solutions when brainstorming together.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">New joiners in a team can give unbiased view of code / approach / architecture: ask them what they think about the code when they join the team before they get used to it and don’t challenge it anymore because they became biased as well.</div>
</div>

---

# Writing Code

Many good development practices are actually about reducing cognitive load. Here we’ll see some:

## Splitting long methods/functions

Let's look at code that could benefit from splitting:

```java
public void processOrder(Order order) {
    if (!order.getItems().isEmpty()) {
        double total = 0;
        for (Item item: order.getItems()) {
            total += item.getPrice();
            if (item.getType() == ItemType.PERISHABLE) {
                scheduleDelivery(item);
                notifyWarehouse(item);
                updateInventory(item);
            }
        }
        if (total > 1000) {
            applyDiscount(total);
        }
        sendConfirmation(order);
    }
}
```

This can be refactored to:

```java
public void processOrder(Order order) {
    if (order.getItems().isEmpty()) {
        return;
    }
    double total = calculateOrderTotal(order);
    handlePerishableItems(order);
    applyDiscountIfEligible(total);
    sendConfirmation(order);
}

private double calculateOrderTotal(Order order) {
    return order.getItems().stream()
        .mapToDouble(Item::getPrice)
        .sum();
}

private void handlePerishableItems(Order order) {
    order.getItems().stream()
        .filter(item -> item.getType() == ItemType.PERISHABLE)
        .forEach(this::processPerishableItem);
}

private void processPerishableItem(Item item) {
    scheduleDelivery(item);
    notifyWarehouse(item);
    updateInventory(item);
}
```

The refactored code is longer but easier to read and to modify because splitting it into multiple functions makes every single function shorter and so it’s less likely to incur in the short term memory capacity limitation; also the `processOrder()` method is shorter and leverage chunking, allowing our short term memory to be relieved.

## Side effects

Side effects are tricky because they can fool the chunking mechanism. Let’s take a look at this snippet:

```java
public void processOrder(Order order) {
    // other code

    ship(order);
    order.setStatus(Status.SHIPPED);

    // other code
}
```

Reading this snippet we might think that the `setStatus` setter will just update the `status` property to the value passed, but looking at the actual code:

```java
public void setStatus(Status status) {
    this.status = status;
    if (status == Status.SHIPPED) {
        sendEmailToCustomer();
    }
}
```

we can see there’s an hidden side effect of sending an email. This issue is tricky because when we see a `setSomething` method, we normally leverage chunking, getting the info from our long term memory telling us that the setter will just update the property and won’t do anything else.

In this case, if moving the email sending out of the method is not possible, at least rename it to something like `setStatusAndSendEmail`, to be sure that other developers (or your future self) are aware of the non-standard behaviour of the method.

## Naming Conventions

Research by [S. Butler et al.](https://oro.open.ac.uk/17007/) shows that proper naming impacts code quality: they found statistically significant associations between flawed identifiers (i.e. violating at least one guideline) and code quality issues reported by FindBugs.

Here are some common naming flaws they suggest to avoid :

| **Name** | **Description** | **Example of flawed identifier(s)** |
| --- | --- | --- |
| Capitalization Anomaly | Identifiers should be appropriately capitalized. | `HTMLEditorKit`, `pagecounter` |
| Consecutive Underscores | Consecutive underscores should not be used in identifier names. | `foo__bar` |
| Dictionary Words | Identifier names should be composed of words found in the dictionary and abbreviations, and acronyms, that are more commonly used than the not abbreviated form. | `strlen` |
| Enumeration Identifier Declaration Order | Unless there are compelling and obvious reasons otherwise, enumeration constants should be declared in alphabetical order. | `enum Card {ACE, EIGHT, FIVE, FOUR, JACK, KING, ...}` |
| External Underscores | Identifiers should not have either leading or trailing underscores. | `_foo_` |
| Identifier Encoding | Type information should not be encoded in identifier names using Hungarian notation or similar | `int iCount;` |
| Long Identifier Name | Long identifier names should be avoided where possible. | `getPolicyQualifiersRejectedNaming` |
| Convention Anomaly | Identifiers should not consist of non-standard mixes of upper and lower case characters. | `FOO_bar` |
| Number of Words | Identifiers should be composed of between two and four words. | `ArrayOutOfBoundsException`, `name` |
| Numeric Identifier Name | Identifiers should not be composed entirely of numeric words or numbers. | `FORTY_TWO` |
| Short Identifier Name | Identifiers should not consist of fewer than eight characters, with the exception of: c, d, e, g, i, in, inOut, j, k, m, n, o, out, t, x, y, z | `name` |

## Pair Programming

Pair programming can distribute the cognitive load between two people, the driver and the navigator: while the driver thinks only about the implementation of the solution concentrating on syntax, algorithms and logic, the navigator thinks about the overall goals/requirements and can review the code written by the driver. In this way, part of the cognitive load is on the driver and part is on the navigator, lowering it for both.

## Documentation

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1746175388949/3233eab1-a7b1-4c09-8fa3-7553dda47218.png align="left")

*Source: https://www.commitstrip.com/en/2021/11/10/no-documentation*

Documentation is another tool for lowering cognitive load, because we can read the explanation of the code, instead of querying our mental model to understand what that code is doing and why. As the CommitStrip comic notes, we often joke about documentation, but it's essential—especially when it's consistent.

Salvatore Sanfilippo, in his [Writing system software: code comments](http://antirez.com/news/124) article, defines several types of comments, some of which are useless, if not harmful (especially if comments are not updated together with code changes, thing that unfortunately happens too often).

Let's look at an example of good commenting (taken from Salvatore’s article):

```c
if (idle > server.repl_backlog_time_limit) {
	/* When we free the backlog, we always use a new
	 * replication ID and clear the ID2. This is needed
	 * because when there is no backlog, the master_repl_offset
	 * is not updated, but we would still retain our replication
	 * ID, leading to the following problem:
	 *
	 * 1. We are a master instance.
	 * 2. Our replica is promoted to master. It's repl-id-2 will
	 *    be the same as our repl-id.
	 * 3. We, yet as master, receive some updates, that will not
	 *    increment the master_repl_offset.
	 * 4. Later we are turned into a replica, connect to the new
	 *    master that will accept our PSYNC request by second
	 *    replication ID, but there will be data inconsistency
	 *    because we received writes. */
	changeReplicationId();
	clearReplicationId2();
	freeReplicationBacklog();
	serverLog(LL_NOTICE,
	    "Replication backlog freed after %d seconds "
	    "without connected replicas.",
	    (int) server.repl_backlog_time_limit);
}
```

this snippet is part of [replication.c](https://github.com/redis/redis/blob/6c5e263d7bd581767d36a7d84a4124c38713db3c/src/replication.c#L3863) in Redis source code and the comment clearly explains why we should take care of that condition; without that comment it would be a lot more difficult and time consuming to understand why it behaves that way.

On the other hand, look at this code (from Trisha Gee’s article [Do we need comments in our code](https://trishagee.com/2021/05/14/do-we-need-comments-in-our-code/)):

```java
// check if the restaurant actually exists
if (restaurant == null) {
    throw new RestaurantNotFoundException(booking.getRestaurantId());
}
// check if the number of diners in the booking is more than the number of seats in the restaurant
if (restaurant.capacity() < booking.getNumberOfDiners()) {
    throw new NoAvailableCapacityException("Number of diners exceeds available restaurant capacity");
}
// check the restaurant is open on the day of the booking
if (!restaurant.openingDays().contains(booking.getDate().getDayOfWeek())) {
    throw new RestaurantClosedException("Restaurant is not open on: " + booking.getDate());
}
// find all the bookings for that day and check that with all the booked diners the restaurant still has
// space for the new booking diners
List allByRestaurantIdAndDate = repository.findAllByRestaurantIdAndDate(booking.getRestaurantId(),
booking.getDate());
int totalDinersOnThisDay = allByRestaurantIdAndDate.stream().mapToInt(Booking::getNumberOfDiners).sum();
if (totalDinersOnThisDay + booking.getNumberOfDiners() > restaurant.capacity()) {
    throw new NoAvailableCapacityException("Restaurant all booked up!");
}
// if we got this far, the booking is valid and we can save it
return repository.save(booking);
```

in this case the comments don’t really add much information: the code is clear enough thanks to meaningful variable and method names (and the intrinsic simplicity of the process, at least compared to Redis distributed sync mechanism).

---

# The Flow

What happens when the code we're writing is neither too easy nor too complex, and we don't have any external distractions? We enter what M. Csíkszentmihályi called "[The Flow](https://www.researchgate.net/publication/224927532_Flow_The_Psychology_of_Optimal_Experience)", a state of pure focus where time flies and we experience happiness and satisfaction. According to DeMarco and Lister in "[Peopleware](https://www.dorsethouse.com/books/pw.html)," it takes around 15 minutes to reach the Flow state: this means that if an engineer is interrupted once per hour, their productivity drops by 25%.

## How to Enter the Flow

Organize your time:

* Arrange with the team for reserved coding time
    
* Know your productive hours (early bird or night owl?)
    
* Set up no-meeting days or half days to avoid interruptions
    
* Schedule meetings close together so that the rest of the day is uninterrupted
    

## How to Stay in the Flow

Avoid distractions:

* Signal when concentrated (status on Slack/Teams)
    
* Shut down notifications (yes, on the mobile too)
    
* In the office, use hoodies/earphones/signs on the chair
    
* Use fullscreen or no-distraction mode
    
* Maintain focus with the Pomodoro technique (this works for some but it kills the Flow for others, experiment if it works for you!)
    

Reduce tedious tasks:

* Use IDEs / AI tools for writing trivial code
    
* Automate repetitive processes
    

---

# Testing

Tests are of paramount importance for making sure we’re not introducing regressions, and so - if we want to stay in the flow - we need immediate feedback from tests. When writing code, ideally you should have:

* Unit tests that run in under 10 seconds (you can partition your project/tests to achieve this)
    
* Integration tests that complete within 20/30 seconds
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">The timings I provided are the ones that allow me to stay into the flow, but remember: we're all different. What works for a person may not work for another. Experiment and find what works for you and for your team!</div>
</div>

At a later stage you can have:

* End-to-end testing on CI/CD pipelines
    
* Smoke testing after deployment
    

but that’s usually after committing, so you’re already out of the Flow.

This kind of testing strategy is called “Pyramid Testing” because there’s a large base of unit testing, a smaller set of integration tests and a few end to end tests:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1745441990287/6b27682d-1354-4f6a-922b-fbd8e1957e6e.png align="center")

This strategy doesn’t work well in all the contexts. There are other testing strategies which can be more suitable to the project we’re working on: Ramona Schwering wrote an interesting [article](https://web.dev/articles/ta-strategies) about testing strategies if you wanna know more about this topic (the pyramid picture is taken from that article).

But whatever testing strategy you adopted, try to keep the running time of the tests you need while developing to a maximum of ten/twenty seconds (maybe you’ll need to partition your tests, to run them in local, or some other approach to make them run faster).

---

# Code Reviews

It is now a *de facto* standard to have the code reviewed by other team members before committing on trunk. In order to be more efficient and lower our cognitive load, when reviewing other team members’ code:

* Limit reviews to 200-400 lines of code per session (again, this is very personal, find yours)
    
* Schedule reviews during our peak cognitive hours, not when when you’re tired
    
* Use checklists to reduce the cognitive burden of remembering what to look for (i.e. [OWASP checklist](https://github.com/0xRadi/OWASP-Web-Checklist))
    

---

# Rest and Recovery

After having seen how our brain works, we also have to mention that in order to make it work at its best, our brain needs rest. As Matthew Walker explains in [Why We Sleep](https://www.penguin.com.au/books/why-we-sleep-9780141983769/extracts/2487-why-we-sleep), good sleep is essential for cognitive performance and memory consolidation (which usually happens when sleeping): we can put in place all the suggestions explained in this article, but if we slept three hours last night, it’s very unlikely we’re going to do a good job.

---

### Quiz

Do you remember the sequence of numbers I asked to memorize?

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Try to recall the sequence we saw at the beginning of the article</div>
</div>

The sequence was

$$9\qquad5\qquad 8\qquad \qquad 6\qquad 5\qquad 5\qquad 3\qquad 6$$

If you recalled it, congratulations, you just experienced a transition from short term memory to long term memory! With this recall you strengthened this number even more and it’s likely that you’re going to remember it for some days.

---

# Conclusion

Understanding cognitive science can make us better software engineers. By recognizing the limitations of our short-term memory, reducing cognitive load, facilitating flow states, and giving our brains proper rest, we can write better code more efficiently and with greater satisfaction.

The next time you're struggling with a complex system or getting frustrated with poorly written code, remember: our brains have limits, but we can work with these limits rather than against them.