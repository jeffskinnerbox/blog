<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


--------


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

# The Prior
What Is Prior Probability?
Prior probability, often simply called "the prior" in Bayesian statistics, is the probability of an event before new data is collected.
This is the best rational assessment of the probability of an outcome based on
the current knowledge before an experiment is performed.

* [Prior And Posterior - Intro to Statistics](https://www.youtube.com/watch?v=o2Tpws5C2Eg)
* [How Bayes Theorem works](https://www.youtube.com/watch?v=5NMxiOGL39M)

# Bayes Theorem
* [Computational Physics with Python: Bayes Theorem](https://medium.com/@_monitsharma/computational-physics-with-python-bayes-theorem-fdeb3af01f7)

# Two-Child Problem
* [The Probability Paradox: The Mind-Boggling Two-Child Problem Explained](https://medium.com/intuition/the-probability-paradox-the-mind-boggling-two-child-problem-explained-fcdeed38f5b1)