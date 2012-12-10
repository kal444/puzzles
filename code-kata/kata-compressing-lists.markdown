
I have a list, say something like [4, 4, 4, 4, 2, 2, 2, 3, 3, 2, 2, 2, 2, 1, 1, 1, 5, 5], which consists of varying repetitions of integers. (We can assume that it's always numbers, and the use of the term "list" here is generic—it could be a list, array, or some other collection class, your choice.) 

The goal is to take this list of numbers, and "compress" it down into a (theoretically smaller) list of numbers in pairs, where the first of the pair is the occurrence number of the value, which is the second number. 

So, since the list above has four 4's, followed by three 2's, two 3's, four 2's, three 1's and two 5's, it should compress into [4, 4, 3, 2, 2, 3, 4, 2, 3, 1, 2, 5].

Using your functional language of choice, implement a solution. (No looking at Rick's solution first, by the way—that's cheating!) Feel free to post proposed solutions here as comments, by the way.

This is a pretty easy challenge, but I wanted to try and solve it in a functional mindset, which the challenger had never seen before. 

I also thought it made for an interesting challenge for people who've never programming in functional languages before, because it requires a very different approach than the imperative solution.

Extensions to the kata (a.k.a. "extra credit"):

* How does the implementation change (if any) to generalize it to a list of any particular type? (Assume the list is of homogenous type—always strings, always ints, always whatever.)
* How does the implementation change (if any) to generalize it to a list of any type? (In other words, a list of strings, ints, Dates, whatever, mixed together within the list: [1, 1, "one", "one", "one", ...] .)
* How does the implementation change (if any) to generate a list of two-item tuples (the first being the occurence, the second being the value) as the result instead? Are there significant advantages to this?
* How does the implementation change (if any) to parallelize/multi-thread it? For your particular language how many elements have to be in the list before doing so yields a significant payoff?

By the way, some of the extension questions make the Kata somewhat interesting even for the imperative/O-O developer; have at, and let me know what you think.
