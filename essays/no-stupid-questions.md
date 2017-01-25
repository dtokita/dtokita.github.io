---
layout: essay
type: essay
published: true
title: No Stupid Questions
date: 2017-01-18
labels:
  - Software Engineering
  - Questions
---

## There really are stupid questions.##

<img class="ui tiny left circular floated image" src="../images/questions.png">

We as human beings have the ability to communicate in a whole variety of ways. We have cell phones, text messages, radio signals and of course our own voices. However, it doesn't matter how sophisticated the technology if the users communicate ineffectively. 

The person who asks the question clearly has a need for information. However, if his need is unclear, then of course the answers he/she recieves will also be unclear. As a result, the person who asked the question is unhappy, and the time of the person who asked the question was wasted.

With the dawn of the information age with internet and other resources, there is information readily available at many's finger tips. Of course in order for the information to be on the internet in the first place, the question had to be asked originally. However, if the question has been answered before, and a simple google search would yield the answer, why waste someone else's time answering a question that already has been answered.

This is a good example of a poor question and as a result recieves a poor answer.

```
Question:
This program will need to handle all grades for 10 students. Each student has a first and last name, an id number, 3 homework grades, 3 labs grades, 3 test grades, and 1 final exam grade. display the final course grade in both numbered and letter version

The equation only works for the first set of grades then it adds a little bit to the next average I just can't figure out whats wrong.

Answer:
You haven't reset these variables to zero.
```
Keep in mind, in the original post, no source code was included. So many of the responses included were asking for the code. However, even after the code was posted, the response was vague, unspecific, and non informative, likely a product of a poor question.

## Why it is so important to ask good questions. Please.##

It is in the best interest of both parties to ask and answer good questions. When you ask good questions you give yourself an opportunity for good answers. Specifically for software engineers, questions are often complex and the answers just as complex.

Clarity is one of the most important keys to successful questions and answers. If it is clear what you want, it will be clear and simple to answer. Also, showing one's own attempts at a solution and research towards the question is important and also ties into the clarity of the question. If the people who answer the questions can see what you already tried, they can get a better idea of what you don't understand.

It is important to ask the right people. If you ask a questions that is completely irrelevant to them, it becomes a stupid question to them. Therefore knowing who you are asking is an important factor in asking a good question.

This is a very effective question and answer. The question and the level of understand was clear and the answer was direct, helpful and correct.

```
Question:
Here is a piece of C++ code that seems very peculiar. For some strange reason, sorting the data miraculously makes the code almost six times faster.

#include <algorithm>
#include <ctime>
#include <iostream>

int main()
{
    // Generate data
    const unsigned arraySize = 32768;
    int data[arraySize];

    for (unsigned c = 0; c < arraySize; ++c)
        data[c] = std::rand() % 256;

    // !!! With this, the next loop runs faster
    std::sort(data, data + arraySize);

    // Test
    clock_t start = clock();
    long long sum = 0;

    for (unsigned i = 0; i < 100000; ++i)
    {
        // Primary loop
        for (unsigned c = 0; c < arraySize; ++c)
        {
            if (data[c] >= 128)
                sum += data[c];
        }
    }

    double elapsedTime = static_cast<double>(clock() - start) / CLOCKS_PER_SEC;

    std::cout << elapsedTime << std::endl;
    std::cout << "sum = " << sum << std::endl;
}
Without std::sort(data, data + arraySize);, the code runs in 11.54 seconds.
With the sorted data, the code runs in 1.93 seconds.
Initially, I thought this might be just a language or compiler anomaly. So I tried it in Java.

import java.util.Arrays;
import java.util.Random;

public class Main
{
    public static void main(String[] args)
    {
        // Generate data
        int arraySize = 32768;
        int data[] = new int[arraySize];

        Random rnd = new Random(0);
        for (int c = 0; c < arraySize; ++c)
            data[c] = rnd.nextInt() % 256;

        // !!! With this, the next loop runs faster
        Arrays.sort(data);

        // Test
        long start = System.nanoTime();
        long sum = 0;

        for (int i = 0; i < 100000; ++i)
        {
            // Primary loop
            for (int c = 0; c < arraySize; ++c)
            {
                if (data[c] >= 128)
                    sum += data[c];
            }
        }

        System.out.println((System.nanoTime() - start) / 1000000000.0);
        System.out.println("sum = " + sum);
    }
}
With a somewhat similar but less extreme result.

My first thought was that sorting brings the data into the cache, but then I thought how silly that is because the array was just generated.

What is going on?
Why is a sorted array faster to process than an unsorted array?
The code is summing up some independent terms, and the order should not matter.

Answer:
You are a victim of branch prediction fail.

What is Branch Prediction?

Consider a railroad junction:
Now for the sake of argument, suppose this is back in the 1800s - before long distance or radio communication.

You are the operator of a junction and you hear a train coming. You have no idea which way it is supposed to go. You stop the train to ask the driver which direction they want. And then you set the switch appropriately.

Trains are heavy and have a lot of inertia. So they take forever to start up and slow down.

Is there a better way? You guess which direction the train will go!

If you guessed right, it continues on.
If you guessed wrong, the captain will stop, back up, and yell at you to flip the switch. Then it can restart down the other path.
If you guess right every time, the train will never have to stop.
If you guess wrong too often, the train will spend a lot of time stopping, backing up, and restarting.

Consider an if-statement: At the processor level, it is a branch instruction:
You are a processor and you see a branch. You have no idea which way it will go. What do you do? You halt execution and wait until the previous instructions are complete. Then you continue down the correct path.

Modern processors are complicated and have long pipelines. So they take forever to "warm up" and "slow down".

Is there a better way? You guess which direction the branch will go!

If you guessed right, you continue executing.
If you guessed wrong, you need to flush the pipeline and roll back to the branch. Then you can restart down the other path.
If you guess right every time, the execution will never have to stop.
If you guess wrong too often, you spend a lot of time stalling, rolling back, and restarting.

This is branch prediction. I admit it's not the best analogy since the train could just signal the direction with a flag. But in computers, the processor doesn't know which direction a branch will go until the last moment.

So how would you strategically guess to minimize the number of times that the train must back up and go down the other path? You look at the past history! If the train goes left 99% of the time, then you guess left. If it alternates, then you alternate your guesses. If it goes one way every 3 times, you guess the same...

In other words, you try to identify a pattern and follow it. This is more or less how branch predictors work.

Most applications have well-behaved branches. So modern branch predictors will typically achieve >90% hit rates. But when faced with unpredictable branches with no recognizable patterns, branch predictors are virtually useless.

Further reading: "Branch predictor" article on Wikipedia.

As hinted from above, the culprit is this if-statement:

if (data[c] >= 128)
    sum += data[c];
Notice that the data is evenly distributed between 0 and 255. When the data is sorted, roughly the first half of the iterations will not enter the if-statement. After that, they will all enter the if-statement.

This is very friendly to the branch predictor since the branch consecutively goes the same direction many times. Even a simple saturating counter will correctly predict the branch except for the few iterations after it switches direction.

Quick visualization:

T = branch taken
N = branch not taken

data[] = 0, 1, 2, 3, 4, ... 126, 127, 128, 129, 130, ... 250, 251, 252, ...
branch = N  N  N  N  N  ...   N    N    T    T    T  ...   T    T    T  ...

       = NNNNNNNNNNNN ... NNNNNNNTTTTTTTTT ... TTTTTTTTTT  (easy to predict)
However, when the data is completely random, the branch predictor is rendered useless because it can't predict random data. Thus there will probably be around 50% misprediction. (no better than random guessing)

data[] = 226, 185, 125, 158, 198, 144, 217, 79, 202, 118,  14, 150, 177, 182, 133, ...
branch =   T,   T,   N,   T,   T,   T,   T,  N,   T,   N,   N,   T,   T,   T,   N  ...

       = TTNTTTTNTNNTTTN ...   (completely random - hard to predict)
So what can be done?

If the compiler isn't able to optimize the branch into a conditional move, you can try some hacks if you are willing to sacrifice readability for performance.

Replace:

if (data[c] >= 128)
    sum += data[c];
with:

int t = (data[c] - 128) >> 31;
sum += ~t & data[c];
This eliminates the branch and replaces it with some bitwise operations.

(Note that this hack is not strictly equivalent to the original if-statement. But in this case, it's valid for all the input values of data[].)

Benchmarks: Core i7 920 @ 3.5 GHz

C++ - Visual Studio 2010 - x64 Release

//  Branch - Random
seconds = 11.777

//  Branch - Sorted
seconds = 2.352

//  Branchless - Random
seconds = 2.564

//  Branchless - Sorted
seconds = 2.587
Java - Netbeans 7.1.1 JDK 7 - x64

//  Branch - Random
seconds = 10.93293813

//  Branch - Sorted
seconds = 5.643797077

//  Branchless - Random
seconds = 3.113581453

//  Branchless - Sorted
seconds = 3.186068823
Observations:

With the Branch: There is a huge difference between the sorted and unsorted data.
With the Hack: There is no difference between sorted and unsorted data.
In the C++ case, the hack is actually a tad slower than with the branch when the data is sorted.
A general rule of thumb is to avoid data-dependent branching in critical loops. (such as in this example)

Update :

GCC 4.6.1 with -O3 or -ftree-vectorize on x64 is able to generate a conditional move. So there is no difference between the sorted and unsorted data - both are fast.
VC++ 2010 is unable to generate conditional moves for this branch even under /Ox.
Intel Compiler 11 does something miraculous. It interchanges the two loops, thereby hoisting the unpredictable branch to the outer loop. So not only is it immune the mispredictions, it is also twice as fast as whatever VC++ and GCC can generate! In other words, ICC took advantage of the test-loop to defeat the benchmark...
If you give the Intel Compiler the branchless code, it just out-right vectorizes it... and is just as fast as with the branch (with the loop interchange).
This goes to show that even mature modern compilers can vary wildly in their ability to optimize code...
```
We can see that the person who asked his question clearly made honest attempts at solving the problem and tried experimenting on his own. He is very clear in what he wants, adding in a lot of details. Therefore the answer that he recieves is just as detailed and clear.

## You don't have to do it alone.##

I really don't want to discourage anyone from asking questions. Questions are the way that people learn and discover new things. However, there are certainly dumb questions that communicate poorly or waste time. Time and effort that could be used to create new ideas, ask better questions, and communicate effectively.

As a result, my final stance on this is that questions are necessary and even welcome up to a point. If sufficient effort and understanding is shown and what is being questioned is clear, that question deserves to be answered. I certainly would not be where I am today without asking questions, however, no one is perfect, and a stupid one comes out every so often. It happens.
