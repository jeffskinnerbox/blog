<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->

<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg"
        title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>

---------------

* [We may question the universe into existence](https://medium.com/the-infinite-universe/we-may-question-the-universe-into-existence-8100c83edf34)
* [Untangling entanglement](https://aeon.co/essays/our-simple-magic-free-recipe-for-quantum-entanglement?utm_source=Aeon+Newsletter&utm_campaign=4e81f927d4-EMAIL_CAMPAIGN_2023_06_30&utm_medium=email&utm_term=0_-b43a9ed933-%5BLIST_EMAIL_ID%5D)
* [collider bias](https://www.google.com/search?q=collider+bias&oq=collider+bias&gs_lcrp=EgZjaHJvbWUyBggAEEUYOdIBCjM2MjI1MWowajeoAgCwAgA&sourceid=chrome&ie=UTF-8#ip=1)
* [Causality: What is Causality?](https://www.youtube.com/playlist?list=PLcTBLulJV_AKmUTH-nUsxxFyRQoWnUzxU)

So what is probibility and what does it mean to be random?
I want to explain and demonstrate these seemingly simple concepts to show how they are not so simple,
and how they are a source of much confusion & deception.

Python Simulation of Monty Hall Problem = [Don’t Switch! Why Mathematicians’ Answer to the Monty Hall Problem is Wrong](https://ima.org.uk/4552/dont-switch-mathematicians-answer-monty-hall-problem-wrong/)

ChatGPT (March 2023 version) request of "Python Simulation of Monty Hall Problem":
_The simulation uses a random strategy where the contestant's initial choice is random, and the host's reveal and the contestant's decision to switch or not are also random. The simulation runs for a specified number of times (in this case, 10,000), and the results are printed showing the percentage of wins with and without switching doors. According to the Monty Hall problem, the optimal strategy is to always switch doors after the host reveals a door without the prize, as it results in a higher probability of winning._

```python
import random

# to assure we can reproduce results, provide a seed

# Function to simulate the Monty Hall problem
def monty_hall_simulation(num_simulations):
    num_wins_with_switch = 0
    num_wins_without_switch = 0

    for _ in range(num_simulations):
        # Three doors: Door 1, Door 2, Door 3
        doors = [1, 2, 3]
        # Randomly place the prize behind one of the doors
        prize_door = random.choice(doors)
        # Contestant chooses one door
        contestant_choice = random.choice(doors)

        # Host reveals a door that does not have the prize and is not chosen by the contestant
        remaining_doors = list(set(doors) - set([contestant_choice, prize_door]))
        host_reveal = random.choice(remaining_doors)

        # Contestant switches their choice to the remaining unopened door
        contestant_choice = list(set(doors) - set([contestant_choice, host_reveal]))[0]

        # Check if the contestant wins with switch
        if contestant_choice == prize_door:
            num_wins_with_switch += 1

        # Check if the contestant wins without switch
        if contestant_choice == contestant_choice:
            num_wins_without_switch += 1

    # Calculate win percentages for both strategies
    win_percentage_with_switch = num_wins_with_switch / num_simulations * 100
    win_percentage_without_switch = num_wins_without_switch / num_simulations * 100

    print("Results after {} simulations:".format(num_simulations))
    print("Wins with switch: {} ({}%)".format(num_wins_with_switch, win_percentage_with_switch))
    print("Wins without switch: {} ({}%)".format(num_wins_without_switch, win_percentage_without_switch))


# Run the simulation with 10,000 simulations
monty_hall_simulation(10000)
```

### Monty Hall Problem

* [The Monty Hall Problem: Dividing Statisticians since 1975](https://medium.com/@nahmed3536/the-monty-hall-problem-dividing-statisticians-since-1975-8f298875dcf)
* [The Myth of the Monty Hall Problem](https://medium.com/@danielbier/the-myth-of-the-monty-hall-problem-8735fee7e2b1)
* [Why most explanations of the Monty Hall problem are (partially) wrong](https://medium.com/@analog_cs/why-most-explanations-of-the-monty-hall-problem-are-partially-wrong-e9216ec4d747)
* [Don’t Switch! Why Mathematicians’ Answer to the Monty Hall Problem is Wrong](https://ima.org.uk/4552/dont-switch-mathematicians-answer-monty-hall-problem-wrong/)
* [What Happened to the World’s Smartest Woman After She Solved a Math Question?](https://ali.medium.com/what-happened-to-the-worlds-smartest-woman-after-she-solved-a-math-question-019943967383)
* [Marilyn vos Savant](https://en.wikipedia.org/wiki/Marilyn_vos_Savant)
* [The Monty Hall problem but the host sucks at his job](https://www.youtube.com/watch?v=pqGmUB3yjrQ)

### Monty Hall Problem ... stated Differently

* [This May Be The Most Counterintuitive Probability Paradox I've Ever Seen | Can you spot the error?](https://www.youtube.com/watch?v=bDZieLmya_I)

# The Game's Actors

Traditionally, the only actors are Monty & the contestant.
What if the goats made a contribution by make noise and you have some probability to accurate locate the door which it is behind?

# Game Formulation

The traditional formulation for the Monty Hall Problem is 3 doors, 2 goats, and 1 car.
But you could choose other sizes, such as N doors, N-1 goats, and 1 car,
you find wise decision making becomes more transparent.
What if all non-car doors didn't have a goats but something of substantial value but not as valuable as a car?

* The game can be played with 3 to 100 doors.
* The game can be played with something of substantial value and a single car (preferred)

# Monty’s & Contestant's objectives and motivations

* Monty has to manage the game; that is, he has to ensure that all the contestants have a reasonable hearing and that it finishes on time.
* Monty has to entertain the audience; this is likely to mean, among other things, that the contestants win cars reasonably often.

* The contestant is free to pick any door they wish.
* Monty will always open a door.
* Monty never opens the door you have chosen.
* Monty never opens the door with the car behind it.
* The car is equally likely to be behind any door.
* Given a choice of doors, Monty chooses at random.

Monty is not likely to want to give away too many cars because of the cost to his employers.

What if Monty randomly picked a door to open, including the door with a car?
What if Monty only told you which door has a goat, did not show you, and Monty has some probability of lying?

# The Monty Fall Problem

As before, you are faced with three doors.
Two of them hide a goat, one of them hides a car,
and you have to pick one of them.
You win whatever is behind that door.
Let’s say you pick door 2.

The host then walks past the doors,
trips over his own foot,
and accidentally opens another door, say door 1.
It turns out there is a goat behind door 1.

“Oops,” the host says.“My bad.
But now that you know there is a goat behind door 1,
would you like to switch to door 3?”

Is it in your best interest to switch?

* [How to Solve the Monty Fall Problem](https://medium.com/street-science/how-to-solve-the-monty-fall-problem-ed68d78d8795)

---------------

# Bertrand's Box Paradox

* [Ranking Paradoxes, From Least to Most Paradoxical](https://www.youtube.com/watch?v=1vJsWKg2o1w)

---------------

# The Prior

What Is Prior Probability?
Prior probability, often simply called "the prior" in Bayesian statistics, is the probability of an event before new data is collected.
This is the best rational assessment of the probability of an outcome based on
the current knowledge before an experiment is performed.

* [Prior And Posterior - Intro to Statistics](https://www.youtube.com/watch?v=o2Tpws5C2Eg)
* [How Bayes Theorem works](https://www.youtube.com/watch?v=5NMxiOGL39M)

# Bayes Theorem

* [Computational Physics with Python: Bayes Theorem](https://medium.com/@_monitsharma/computational-physics-with-python-bayes-theorem-fdeb3af01f7)

# Two-Child Problem (aka Boy or Girl Paradox)

Suppose a friend of yours has two children,
but you cannot remember their genders.
One day, he implies that one of the children is male.
Now here’s the question:
What is the probability that the other child is female?

You may assume for this question:

* Only options are male/female
* Order is not important

* [The Probability Paradox: The Mind-Boggling Two-Child Problem Explained](https://medium.com/intuition/the-probability-paradox-the-mind-boggling-two-child-problem-explained-fcdeed38f5b1)
* [Cheeky probability problems to irritate your friends](https://medium.com/tales-to-infinity/a-fiendish-little-probability-problem-4404dbd3629)

What if you knew one of the children was female?
What if order of the childern was known?
What if you knew one of the children's name?
What if you knew one of the children's day of week they where born?

* [This May Be The Most Counterintuitive Probability Paradox I've Ever Seen | Can you spot the error?](https://www.youtube.com/watch?v=bDZieLmya_I)
* [he Boy or Girl Probability Paradox Resolved | It was never really a paradox](https://www.youtube.com/watch?v=ElB350w8iJo)
* [Boy or Girl paradox](https://en.wikipedia.org/wiki/Boy_or_Girl_paradox)

# Boy or Girl Paradox With Cards or Coins

* [Just 3 questions/puzzles that seem obvious but aren't](https://www.youtube.com/watch?v=YCRxwClpUGk)

# Bertrand’s Box Paradox

* [How To Make Sense Of Bertrand’s Box Paradox?](https://streetscience.net/how-to-make-sense-of-bertrands-box-paradox/)
* [Probability Puzzle Paradox: Which Boxes To Take?](https://www.wmbriggs.com/post/54440/)

# Coin Flipping Paradox

* [The coin flip conundrum - Po-Shen Loh](https://www.youtube.com/watch?v=IAiNqQi30-Y)
* [Counter-Intuitive Probability. Coin Flips To HH Versus HT Are Not The Same!](https://www.youtube.com/watch?v=--mxW3jDlGk)
* [Coin Flipping Paradox](https://www.youtube.com/watch?v=F1ccNKQx4fk)
* [A Coin-Tossing Conundrum](https://arxiv.org/pdf/1710.01298.pdf)
* [Probability is just...really weird](https://www.youtube.com/watch?v=zczGnnM05TQ)
* [The Coin Flip Game that Stumped Twitter: Alice HH vs Bob HT](https://www.youtube.com/watch?v=BAiuFOwhAWw)

# The Friendship Paradox

* [The Friendship Paradox](https://www.youtube.com/watch?v=GEjhO65FYks)

# Sleeping Beauty Problem

* [193,340 People Agree With Me, 85,660 Disagree](https://www.youtube.com/watch?v=XeSu9fBJ2sI)
* [Sleeping Beauty Paradox - Numberphile](https://www.youtube.com/watch?v=cW27QJYNXtU)
* [Self-locating belief and the Sleeping Beauty problem](https://www.princeton.edu/~adame/papers/sleeping/sleeping.pdf)
* [The Most Controversial Problem in Philosophy](https://www.youtube.com/watch?v=XeSu9fBJ2sI)

# Prisoner’s Puzzle

* [A Fascinating Prisoner’s Puzzle](https://www.cantorsparadise.com/a-fascinating-prisoners-puzzle-be874032f43e)
* [Impossible Escape?](http://datagenetics.com/blog/december12014/index.html)
* [The almost impossible chessboard puzzle](https://www.youtube.com/watch?v=as7Gkm7Y7h4)
* [What The Prisoner's Dilemma Reveals About Life, The Universe, and Everything](https://www.youtube.com/watch?v=mScpHTIi-kM)

# Red & Green Ball / A Random Choice Gives You Information

You are given an urn containing 100 balls; n of them are red, and 100-n are green,
where n is chosen uniformly at random in [0, 100].
You take a random ball out of the urn, it’s red and it is discard.
For next ball you pick (out of the 99 remaining), is it more likely to be read or green, or are the two colors equally likely?

One thing I find revealing is that the urn
problem is completely sensitive to the fact that
the number of red balls is chosen according to
what’s called a uniform distribution [that is,
by picking out of a hat]. Choosing a red ball
tells you that you’re probably living in a red
world, but only because I set the problem up
that way.

If you choose the colors of the balls according
to a binomial distribution — where you choose
each ball’s color by flipping a coin — then
knowing the first ball is red gives no
information about the next ball. It’s easy to
modify the starting distribution so that you
get any of the three possible answers — red,
green or equally likely. And since tweaking the
distribution completely changes the answer,
that suggests that your intuition has to be very
sensitive to the setup of the problem.

* [Perplexing the Web, One Probability Puzzle at a Time](https://www.quantamagazine.org/perplexing-the-web-one-probability-puzzle-at-a-time-20240829/)
  * [Daniel Litt’s Probability Puzzle](https://arxiv.org/html/2409.08094v1)

# P-Value

* [P-Value: An Intuitive Explanation for Non-Statisticians](https://towardsdatascience.com/how-to-interpret-p-value-with-covid-19-data-edc19e8483b)

---------------

# Python Simulations

## 3D Animations

* [Web VPython](https://www.glowscript.org/)
  * [Web VPython Road Test](https://rjallain.medium.com/web-vpython-road-test-808a69cac916)

## Physics

* [Dot Physics](https://www.youtube.com/@DotPhysics)

## Manim

Manim is an engine for precise animations, designed for creating explanatory math videos.

* [3Blue1Brown Animation Engine for Explanatory Math Videos](https://github.com/3b1b/manim)
* [How to Create Mathematical Animations like 3Blue1Brown Using Python](https://towardsdatascience.com/how-to-create-mathematical-animations-like-3blue1brown-using-python-f571fb9da3d1)
* [ManimCommunity](https://github.com/ManimCommunity)
* [Manim Documentation](https://docs.manim.community/en/stable/index.html#)

---------------

# Zero-Knowledge Proofs

* [A Beginner's Guide to Zero Knowledge Proofs (ZK Proofs Explained)](https://www.youtube.com/watch?v=_MYpZQVZdiM)
* [How Do You Prove a Secret?](https://www.quantamagazine.org/how-to-prove-you-know-a-secret-without-giving-it-away-20221011/)
* [Computer Scientist Explains One Concept in 5 Levels of Difficulty | WIRED](https://www.youtube.com/watch?v=fOGdb1CTu5c)
* [How Do You Prove a Secret?](https://www.quantamagazine.org/how-to-prove-you-know-a-secret-without-giving-it-away-20221011/)

## Knowledge and Information

Knowledge is awareness, understanding, or skill that you get from experience or education.
Information is the facts or details that are organized and processed to provide context and meaning.
For example, knowing the capital of France is information.

Here are some other differences between information and knowledge:

* **Source** - Information comes from data, while knowledge comes from experience or education.
* **Transferability** - Information is easily transferred using technology, but knowledge is more difficult to transfer because it's unarticulated and requires experience.
* **Reproduction** - Information is easily reproduced at a lower cost, but knowledge is more difficult to reproduce.
* **Predictability** - Information alone is not enough to make predictions, but knowledge can make predictions or inferences.
* **Uniqueness** - Knowledge is unique to each individual.

The relationship between data, information, and knowledge can be thought of as a process that's not uni-directional.
For example, knowledge gained from analyzing information can reveal gaps in the data,
which can lead to changes in how the data is collected or converted into information.

---------------

# The Birthday Paradox

* [Simple Explanation of the Birthday Paradox](https://www.youtube.com/watch?v=OcCRflNM-Xk)
