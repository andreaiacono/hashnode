---
title: "Backtracking explained"
datePublished: Sat Oct 07 2017 10:48:25 GMT+0000 (Coordinated Universal Time)
cuid: clok95wt7000o0ajpedk26m0b
slug: backtracking-explained-7450d6ef9e1a
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1759228252612/4fa81411-5dc3-438f-b91a-a8dffab00668.png
tags: algorithms, backtracking

---

Backtracking is one of my favorite algorithms because of its simplicity and elegance; it doesn’t always have great performance, but the branch-cutting part is really exciting and gives you an idea of the progress in performance while you code.

But let’s first start with a simple explanation. According to Wikipedia:

> **Backtracking** is a general algorithm for finding all (or some) solutions to some computational problems, that incrementally builds candidates to the solutions, and abandons each partial candidate (“backtracks”) as soon as it determines that the candidate cannot possibly be completed to a valid solution.

Once you already have used backtracking, it’s a pretty straightforward definition, but I realize that when you read it for the first time is not that clear (or — at least — it wasn’t to me).

A little example could help us. Imagine having a maze and you want to find if it has an exit (for the sake of precision, algorithms to get out of a maze using graphs are more efficient than backtracking). This is the maze:

![A simple maze with only three junctions](https://cdn.hashnode.com/res/hashnode/image/upload/v1699111962606/37eb917c-3def-4031-8bb5-969fe0c0bd71.png align="center")

where we have labeled the junctions as 1, 2 and 3.

If we want to check every possible path in the maze, we can have a look at the tree of paths, split for every junction stop:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699111964462/7e575f48-d3c7-4fa3-9d90-b9da79596bc8.png align="center")

All the possible paths of the maze

Let’s see a pseudo code for traversing this maze and checking if there’s an exit:

```python
function backtrack(junction):

if is_exit:
    return true

for each direction of junction:
    if backtrack(next_junction):
        return true

return false
```

If we apply this pseudo code to the maze we saw above, we’ll see these calls:

```plaintext
- at junction 1 chooses down       (possible values: [down, up])
    - at junction 3 chooses right  (possible values: [right, up])
         no junctions/exit         (return false)
    - at junction 3 chooses up     (possible values: [right, up])
         no junctions/exit         (return false)
- at junction 1 chooses up         (possible values: [down, up])
    - at junction 2 chooses down   (possible values: [down, left]) 
         the exit was found!       (return true)
```

Please note that every time a line is indented, it means that there was a recursive call. So, when a `no junctions/exit` is found, the function returns a `false` value and goes back to the caller, which resumes to loop on the possible paths starting from the junction. If the loop arrives at the end, that means that from that junction on there’s no exit, and so it returns `false`.

The idea is that we can build a solution step by step using recursion; if during the process we realize that is not going to be a valid solution, then we stop computing that solution and return back to the step before (*backtrack*). In the case of the maze, when we are at a dead-end we are forced to backtrack, but there are other cases in which we could realize that we’re heading to a nonvalid (or not good) solution before having reached it. And that’s exactly what we’re going to see now.

---

Quite a while ago I was gifted one of those puzzles based on shaped pieces (*à la* Tetris) that have to be framed in the form of a square or a rectangle:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699112732608/ec1398e4-dcf3-4fb8-80da-d6b2b506f5c7.png align="center")

After tweaking it for a while I couldn’t come up with a solution, so I decided to write a program to solve the puzzle for me.

I’ve chosen the [Go](https://golang.org/) language and the [Gotk3](https://github.com/gotk3/gotk3) project (a binding to GTK3 libraries) to write a simple GUI application that -given a puzzle in input- uses backtracking to find all the possible solutions.

The main idea of the algorithm is this: we start with an empty frame and then try to place the first piece; since the canvas is empty, it will for sure fit into it; we recursively try to place the second piece (not overlapping the first), and then the third and so on, until either it finds a piece that cannot be placed into the canvas, or there are no more pieces to place. In the first case, we have to go back from that branch of execution (we have to *backtrack*) because it makes no sense going on trying to place the remaining pieces if that one cannot be placed (there’s no valid solution without that piece); in case of no more pieces to place, that means we found a solution, so we can add it to the set of solutions and go on finding other ones.

---

Let’s now consider the very nature of this puzzle: the pieces can be rotated and flipped, so for every piece we have to try all its possible rotations. Given that, here’s the solver function (a lot of details like data structures and other functions are omitted, but the sense should be clear):

%[https://gist.github.com/andreaiacono/e8fbd51e8e7d8320c7faa0e162dbca8b] 

If you want to see the real implementation, head to the GitHub repository: [https://github.com/andreaiacono/GoShapesPuzzle](https://github.com/andreaiacono/GoShapesPuzzle).

Considering a 5x6 model, like this one:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699111966284/478191cc-1390-4cae-a7e7-f5011e986b52.png align="center")

the execution time is not exciting: on my notebook it took 1h18m31s.

Can we do better?

---

Let’s think about what this algorithm does: it places all the pieces in every possible position, even where it makes no sense to do it. For example, this is one of the possible configurations:

![Those little empty spots will never be filled](https://cdn.hashnode.com/res/hashnode/image/upload/v1699111968089/3eb4c642-ed8c-472e-a444-6b26824bf181.png align="center")

Of course, those 1-cell and 2-cell empty spaces (circled in red in the above image) will never be filled because in this model we don’t have any piece small enough to fit into them, and thus the whole branch of computation will eventually fail (meaning that no solution will be found since not all the pieces will be placed on the grid). So, it would be nice to cut the branch as soon as we realize that there’s an empty space smaller than the smaller of the remaining pieces to place.

This can be achieved by adding this check:

%[https://gist.github.com/andreaiacono/623d9b4aab8b01ac44cb1aa5df1df571] 

First, we place the piece we are examining now into the grid, and then we compute the size of every empty area (using a floodfill-like algorithm). At the end of the function, we just return if the minimum empty area is smaller than the smaller remaining piece. So if this function returns *true* that means that this branch of computation will never arrive at a solution, and hence we can cut it.

What we’ve done is add some extra computation (to find the minimum empty space size) to avoid following a branch that will never arrive at a solution; more in general, it depends on the problem we’re trying to solve if it makes sense to add the extra computation or not because it could be something that worsens the general performance of the algorithm.

In our case, this extra computation resulted in a total computation time cut from 1h18m31s to 6m19s: a 12.5x increment in performance!

Can we do better?

---

If we look at the main loop of the solver, we realize that the same configuration is computed multiple times. Let’s suppose that the solver starts placing piece no. 1 in (0,0) and then piece no.2 in (3,0); when the branch of piece no.1 as the first piece will be over, the solver will start placing piece no.2, and after trying other positions it will place it in (3,0); going on computing that branch it soon will place piece no.1 in (0,0). But, hey, we already computed a configuration with piece no. 0 and piece no. 1 in those positions, and hence all the (recursive) configurations following this one. This algorithm can be improved a bit more.

To avoid this, I created a map that maps a string representation of the grid to a boolean (I would have created a Set with another language, but Go doesn’t have it) and this code to check it:

%[https://gist.github.com/andreaiacono/8391f2a2a79b83802fbc7d295f71a086] 

So, every time the solver wants to place a piece, it first checks if it already did it before, and if it did, it just skips this state, otherwise it saves the new state into the map and goes on with that branch. Thanks to this optimization, the total computation time dropped from 6m19s to 1m44: another 3.5x performance increment!

So, from the first implementation we had a 43x performance increase!

If you’re interested in seeing the complete source code and running it, you can find it on Git Hub: [https://github.com/andreaiacono/GoShapesPuzzle](https://github.com/andreaiacono/GoShapesPuzzle).

This article was originally published on [Medium](https://medium.com/@andreaiacono/backtracking-explained-7450d6ef9e1a).