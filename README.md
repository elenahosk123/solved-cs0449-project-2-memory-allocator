Download Link: https://assignmentchef.com/product/solved-cs0449-project-2-memory-allocator
<br>



In this project, you will be implementing a memory allocator. You’ll be making your own versions of the <strong>malloc</strong> and <strong>free</strong> functions! Yay! Fun!

<h2>Materials</h2>

You are given the following source files to begin with. Right click and download these files. <strong>Read the comments inside them thoroughly before getting started.</strong>

<ul>

 <li><a href="/teaching/classes/cs0449/projects/mymalloc.h">mymalloc.h</a></li>

 <li><a href="/teaching/classes/cs0449/projects/mymalloc.c">mymalloc.c</a></li>

 <li><a href="/teaching/classes/cs0449/projects/mydriver.c">mydriver.c</a></li>

 <li><a href="/teaching/classes/cs0449/projects/Makefile">Makefile</a>

  <ul>

   <li><strong>SAFARI USERS:</strong> stop using Safari. But really, it will silently rename this file Makefile.dms and I have no idea why and you need to rename it to just Makefile.</li>

  </ul></li>

 <li><a href="/teaching/classes/cs0449/projects/bigdriver.c">bigdriver.c</a></li>

</ul>

<strong>mymalloc.c</strong><strong> is where you’ll be writing all your code for this project.</strong>

The mydriver.c file contains a main function for you to expand upon. By default it just allocates and frees a single block of memory. As you work on your allocator, you can add more testing code to this driver program to make sure it works.

Makefile is a makefile to make your driver, and eventually, other test file(s) that I give you.

The bigdriver.c file is a driver I made to test your allocator more thoroughly. <strong>READ THE COMMENTS INSIDE IT THOROUGHLY TO HELP DEBUG ANY ISSUES THAT COME UP.</strong>

Although bigdriver.c does a lot of tests, it might not catch all bugs. Look at it closely and add tests if you think it’s not thorough enough. You can change it and submit it along with your mydriver.c.

<h2>Building and running</h2>

<strong>To build everything,</strong> use the following command line:

make mydriver

<strong>Ignoring warnings in this project would be a very, very bad idea.</strong> The Makefile uses -Wall -Werror. Do not remove these. <em>Fix all the warnings. SERIOUSLY.</em>

Then, you should be able to:

./mydriver

You can do the same with bigdriver:

make bigdriver./bigdriver

<h2>Your Task</h2>

You will write my_malloc and my_free which implement a simple memory allocator using a linked list and a <strong>first-fit</strong> allocation scheme. The performance won’t be great, but hey, it’s a class project, not a AAA game engine.

Your my_malloc function will:

<ul>

 <li>Round up the size of the requested allocation to a certain size (I gave you this)</li>

 <li>Try to find a block to reuse, using <strong>first-fit</strong> allocation</li>

 <li>If it found a block, and that block can be split into two smaller blocks, do so</li>

 <li>If it couldn’t find a block, expand the heap by moving the break with sbrk()</li>

 <li>Mark it as used</li>

 <li>Return the pointer to the data part (after the header)</li>

</ul>

Your my_free function will:

<ul>

 <li>Figure out the pointer to the header</li>

 <li>Mark the block free</li>

 <li>Coalesce it with any neighboring blocks on either side</li>

 <li>If it’s the last block on the heap, contract the heap by moving the break with sbrk()</li>

</ul>