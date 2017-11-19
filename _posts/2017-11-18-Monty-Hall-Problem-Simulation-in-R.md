---
layout: post
title:  "Monty Hall problem: Understanding & Simulation in R"
date:   2017-11-18
categories: rnotes
tags: notes
---
I first learn about ([Monty Hall Problem](https://en.wikipedia.org/wiki/Monty_Hall_problem)) a few years ago, but never got around to understand how its solution worked. Today, I stumbled on a reference to it again, and wanted understand it intuitively, without googling the solutions. Here is what I got.

### Problem Description:

The problem describes a game show where there are three doors, there is winning choice (a car in the wikipedia example) behind one door, and there are two losing choices (goats in the wikipedia example) behind the other doors.

The rules of the game are as the following.

-   You first choose a door and let the host know.
-   The host knows which doors have the goats, and opens one of the doors that you have not chosen to reveal a goat.
-   You now have the option of sticking with your original choice or changing your choice to the other remaining door.

The question is whether you are better off sticking to your original choice, or switching to the remaining door as your new choice, or if it doesn't matter.

### Solution:

Apparently an overwhelming majority of the people think that it doesn't matter whether you stick to your original choice or change your choice to the remaining door, as both of them are expected to have 33% chance of success originally, or 50% chance of success after you eliminate a door with the goat. But the right answer is that you are better of changing your choice to the other door.

I took a "frequentist" approach, and tried to understand the outcomes for the two cases when you repeat this experiment 999 times.

-   Let us assume we repeat this experiment 999 times and each time one of the three doors (chosen at random, with uniform probability among the three doors) contains the car, the other two doors contain goats.
-   So when we look at 999 runs of the experiments, Door 1 is expected to contain the car 333 times, goats 666 times. The same is the case for Door 2, and Door 3.
-   Assume we choose Door 1 in the beginning, and the host opens either Door 2 or Door 3 to reveal a goat.
-   **Strategy 1: When we don't change the choice**, we already estimated that the Door is expected to contain the car for 333 out of 999 times, so the winning probability is 1/3.
-   **Strategy 2: When we change the choice**, we always choose the remaining door as our final choice.
    -   In this case, the counting becomes easier if we imagine both Door 2 and Door 3 as one bigger unit, and we are changing our choice ot whiever door is remaining in this unit, after the host opened one dooor in this unit and revealed the goat.
    -   For the total 999 runs, the bigger unit (2 doors together) is expected to contain 2*666 goats, and 2*333 goats.
    -   If the host opens one of the doors in the unit, and lets out a goat in each round, he would have let out 999 goats in total. So, by choosing the other door, we are choosing among 2*666 - 999 = 333 goats, and 2*333 = 666 cars. Hence, the winning probability in this case is 666 / 999 = 2/3.
-   Hence, we can see that we are better off changing the choice to other door (the one other than our initial choice, and the one that the host opened). The winning probability in that case increases from 33% to 66%.

### Simualtion of the problem in R:

To verify the logic, we will try to simulate the problem in R and see if are really better off by always changing our choice.

``` r
library(plyr)

# number of runs
n <- 9999

# make a dataframe containing three columns called door1, door2, door3. 
# Each row should contain two "goat"s and one "car", randomly distributed among three columns
set.seed(123)
car_positions <- sample(1:3,n,replace = TRUE)

# run the experiment chosen number of times
experiment_runs <- ldply(car_positions, function(x) ifelse(1:3 == x,"car","goat"))
names(experiment_runs) <- c("Door1", "Door2", "Door3")

# Display the the first few rows of the dataframe, showing random distribution of the cars
head(experiment_runs)
```

    ##   Door1 Door2 Door3
    ## 1   car  goat  goat
    ## 2  goat  goat   car
    ## 3  goat   car  goat
    ## 4  goat  goat   car
    ## 5  goat  goat   car
    ## 6   car  goat  goat

``` r
# Choose initial choice at random
initial_choices <- sample(1:3,n,replace = TRUE)

# The doors opened by host. 
# Assume that he will open the door with the smallest number that is not the initial choice, and has a goat
doors_opened_by_host <- mapply(function(car_position,initial_choice) 
  (1:3)[((1:3) != car_position) & ((1:3) != initial_choice)][1],
  car_positions, initial_choices)

# alternate_choice
alternate_choices <- mapply(function(door_opened,initial_choice) 
  (1:3)[((1:3) != door_opened) & ((1:3) != initial_choice)][1], 
  doors_opened_by_host, initial_choices)

# Probability of winning with original choice
print(paste0("Probability of winning with original choice is: ", 
             format(sum(car_positions == initial_choices)/n, digits = 3)))
```

    ## [1] "Probability of winning with original choice is: 0.337"

``` r
# Probability of winning after changing the choice after the host reveals a door with a goat
print(paste0("Probability of winning after changing the choice is: ", 
             format(sum(car_positions == alternate_choices)/n, digits = 3)))
```

    ## [1] "Probability of winning after changing the choice is: 0.663"

**It can be seen from the above simulation that the better winning strategy is to *change the choice* after the host reveals a door with a goat.**
