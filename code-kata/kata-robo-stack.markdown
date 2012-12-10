
**Problem**: You work for a manufacturing company, and they have just received their newest piece of super-modern hardware, a highly efficient assembly-line mechanized pneumatic item manipulator, also known in some circles as a "robotic arm". It is driven by a series of commands, and your job is to write the software to drive the arm. The initial test will be to have the arm move a series of blocks around.

 

**Context**: The test begins with _n_ number of blocks, laid out sequentially next to each other, each block with a number on it. (You may safely assume that _n_ never exceeds 25.) So, if _n_ is 4, then the blocks are laid out (starting from 0) as:

    0: 0
    1: 1
    2: 2
    3: 3

The display output here is the block-numbered "slot", then a colon, then the block(s) that are stacked in that slot, lowest to highest in left to right order. Thus, in the following display:

    0:
    1:
    2: 0 1 2 3
    3:

The 3 block is stacked on top of the 2 block is stacked on top of the 1 block is stacked on top of the 0 block, all in slot 2. This can be shortened to the representation [0:, 1:, 2: 0 1 2 3, 3:] for conciseness.

The arm understands a number of different commands, as well as an optic sensor. (Yeah, the guys who created the arm were good enough to write code that knows how to read the number off a block, but not to actually drive the arm. Go figure.) The commands are as follows, where _a_ and _b_ are valid block numbers (meaning they are between 0 and n-1):

    "move a onto b" This command orders the arm to find block a, and return any blocks stacked on top of it to their original position. Do the same for block b, then stack block a on top of b.
    "move a over b" This command orders the arm to find block a, and return any blocks stacked on top of it to their original position. Then stack block a on top of the stack of blocks containing b.
    "pile a onto b" This command orders the arm to find the stack of blocks containing block b, and return any blocks stacked on top of it to their original position. Then the arm must find the stack of blocks containing block a, and take the stack of blocks starting from a on upwards (in other words, don't do anything with any blocks on top of a) and put that stack on top of block b.
    "pile a over b" This command orders the arm to find the stack of blocks containing block a and take the stack of blocks starting from a on upwards (in other words, don't do anything with any blocks on top of a) and put that stack on top of the stack of blocks containing block b (in other words, don't do anything with the stack of blocks containing b, either).
    "quit" This command tells the arm to shut down (and thus terminates the simulation).

Note that if the input command sequence accidentally offers a command where _a_ and _b_ are the same value, that command is illegal and should be ignored.
 
As an example, then, if we have 4 blocks in the state [0: 0, 1: 1, 2: 2, 3: 3], and run a "move 2 onto 3", we get [0: 0, 1: 1, 2:, 3: 3 2]. If we then run a "pile 3 over 1", we should end up with [0: 0, 1: 1 3 2, 2:, 3:]. And so on.

**Input**: n = 10. Run these commands:

    move 9 onto 1
    move 8 over 1
    move 7 over 1
    move 6 over 1
    pile 8 over 6
    pile 8 over 5
    move 2 over 1
    move 4 over 9
    quit

The result should be [0: 0, 1: 1 9 2 4, 2:, 3: 3, 4:, 5: 5 8 7 6, 6:, 7:, 8:, 9:]

Challenges:

* Implement the Towers of Hanoi (or as close to it as you can get) using this system.
* Add an optimizer to the arm, in essence reading in the entire program (up to "quit"), finding shorter paths and/or different commands to achieve the same result.
* Add a visual component to the simulation, displaying the arm as it moves over each block and moves blocks around.
* Add another robotic arm, and allow commands to be given simultaneously. This will require some thought—does each arm execute a complete command before allowing the other arm to execute (which reduces the performance having two arms might offer), or can each arm act entirely independently? The two (or more) arms will probably need separate command streams, but you might try running them with one command stream just for grins. Note that deciding how to synchronized the arms so they don't conflict with one another will probably require adding some kind of synchronization instructions into the stream as well.

