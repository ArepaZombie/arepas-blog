---
layout: post
title: How do I begin?
categories: python
---

A lot of energy and a lot of ideas, but without a consistent plan, I can't do anything. Then let's put out some "objectives" for the first, simple game. This one doesn't need a visual program, just the basics to print and take decisions. Then I can only focus on the algorithms. *How* is this game going to work? Well, I want this game to fulfill these basic functions:

1. There is a character with the basic functions of:
     - Walk (change his position)
     - Attack (enter in a fight)
     - Escape (from a fight)
     - Buy stuff (from a Store)
2. The World will be divided into three (3) zones:
      1. **The Village**: Where the Character can buy stuff, heal and sleep (save the game).
      2. **The Forest**: Where are enemies to hunt. The further you are from the village, the more dangerous the monsters are.
      3. **The Cave**: The Dragon resides here. The final boss. The Character can only enter with a Golden Arepa, a magic food that makes The Character see in the darkness.
3.The progression will be this way:
    - The Character has to fight monsters, and that gives him money, and with the money, he can buy stuff in the Store that makes him stronger. For the beginning, I'll start with three (3) levels of objects. He can buy swords, armor, and boots. This serves to increase the strength (in the attack), the defense (when you get attacked) and the speed (for dodging and running). Besides, every "layer" has a Holy Arepa that increases the total HP.
    - When The Character has the best equipment, he can challenge The Guardian, protector of the Golden Arepa and go to The Cave, fight some more enemies, and then face The Dragon. When The Dragon is dead, the game is over... for now.

These are just the first ideas for the first game, a little simple. And maybe it is not thaaat simple, but I want to focus on the functional part of all of this. The visual part could be done later. Then, I better start working on how to solve every problem I'm putting myself in, and then, let the Golden Arepa shine.

## First Problem: The Character

The first thing I had to do is The Character. For this, I think that the best solution is the simplest: A Class.A Class in Python is a way to create Objects. These objects will have different methods and attributes. For this case, I will create the Class *creature* with various sub-classes: *player*, *monster*, *boss*.

The class *creature* will have the following attributes: HP (health points), AP (attack points), DP (defense points), and SP (speed points).

If it is a *player* then it will also have:

- *equipment*: a dictionary with three keys: *sword*,*armor* and *boots*
- *inventory*: a list that stores other kinds of objects for health restore
- *money*: only an int that stores the money.

The *monster* class only has the attribute of *money*. This is the quantity of money that we will win once he is defeated. And the boss will have *money* and *reward*.

## The Second Problem: Fights

Once I have the Character, he has to do something, otherwise it is just code. And the most important thing about this is the fights. How do I do this? The last answer responds to this one: **Objects**.

When I was learning Python, the objects were a hard theme for me to understand, but right now I love them. They are just so helpful. I will use the OTHER thing that Objects have: **methods**. These are like functions inside the object. I think the best way to do this is with a method in the class *creature* just called *attack*, I think this can work this way:

1. Reads the speed of the attacker and the defender. Then if the attacker is faster, it can dodge. If the defender is faster, the possibility will increase depending on the difference. I think that 25% per point could be fair because 4 points is really fast in this game. I'd adjust it later.

2. Then it reads the defense points of the defender. If the speed is equal, this will cut 0.5 AP per DP. If the attacker is faster, only 0.25.

3. Subtract AP from DP and the result are the points that will be put away from the defender (will add or substract 1, 2 or nothing at random).

Even if the interaction between *creatures* is established, this has to be in an environment called *fight*. I think that this can be created using a function that reads two *creatures* in a loop until one of them dies or runs away.*run* should be another method, based on speed and luck. Maybe it was the same interaction with the dodge. Or *run* as a method can be called in the *attack* one and then it dodges or not. This could work. Maybe...

OK, Stop talking. The mission is here! The path is open! Time to code!
