
# Probability Bayes Rule

## Introduction

In practice, Bayes's formula is very useful when it comes to conditional probabilities. The idea behind the rule is that, when having two events $A$ and $B$ and a conditional event $A\mid B$, you can compute the probability of event $B\mid A$.

## Learning objectives

In this lab, you'll
- learn how to apply Bayes' rule, both in the simple form and the long form
- practice creating two-way tables


## Exercise 1

Each year, 2000 students apply for undergrad programs at Stanford University. Among the applicants, 20% have an SAT score above 1550, 55% have an SAT score between 1450 and 1550 and 25% have an SAT below 1450. 

Obviously, the probability of being admitted grows with the SAT score. People that have an SAT score of 1550 or higher have a probability of 80% of being admitted. For students that have scores between 1450 and 1550 this probability drops to 15%, for students that have an SAT score below 1450 this probability drops to 5%. 

- what is the probability of being admitted?
- what is the probability of having an SAT of over 1550 if you were admitted?

### Solution

$P(S>1550) = 0.2 $

$P(1450 <S< 1550) = 0.55$

$P(S< 1450) = 0.25$


$P(A\mid S >1550) = 0.8 $

$P(A\mid 1450 <S< 1550) = 0.15 $

$P(A\mid S< 1450) = 0.05 $

**what is the probability of being admitted?**

According to the decomposition formula:


```python
P_admitted = 0.2* 0.8 + 0.55 * 0.15 + 0.25*0.05
```

**what is the probability of having an SAT of over 1550 if you were admitted?**


```python
P_1550_given_admitted = (0.2* 0.8)/(P_admitted)
P_1550_given_admitted
```

Recall that the probability of being admitted given an SAT of > 1550 is different! So this is a good illustration to show that generally $P(A\mid B) \neq P(B\mid A)$!

## Exercise 2

There is a disease that affects a proportion of $\gamma$ of the human population. 

Having the disease is affected by a genetic factor, and we know that the joint probability of you and your father having the disease is equal to $\delta$.

Now our question is: given that your father doesn't have the disease, what is the probability that you won't get the disease? Create a two-way table to solve this:

$P(A)$ = You have the disease

$P(B)$ = Your dad has the disease

|   |$A$  |$A^c$ | + |
|---|---|---|---|
| $B$  | $\delta$  | ?  | ? | 
| $B^c$ | ?  |  ? |  ? | 
| +  | $\gamma$  |  ? |1   | 

## solution

The key point to know here is that $P(A) = P(B)$!!

And $P(A \cap B)= \delta$

|   |$A$ &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp;&nbsp; |  $A^c$ &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;  &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  | $+$     &nbsp; &nbsp; &nbsp; &nbsp;&nbsp; &nbsp; &nbsp;&nbsp;     |
|---|---|:---: |---|
| $B$   | $\delta$  | $(\gamma-\delta)$  | $\gamma$  | 
| $B^c$ | $(\gamma-\delta)$ | $1-2\gamma+\delta$  | $1-\gamma$ | 
|   $+$   | $\gamma$  |  $1-\gamma$  | 1  | 

Then, $P(A^c \mid B^c) = \dfrac{P(A^c \cap B^c)}{P(B^c)} = \dfrac{1-2\gamma+\delta}{1-\gamma}$

## Exercise 3

Now, let the probability of having the disease be 0.065 and the joint probability of a person and their father having the disease be 0.01, what is the probability that you don't have the disease given that your father doesn't have it?


```python
prob_no_disease = (1-2*0.065+0.01)/(1-0.065)
prob_no_disease # correct answer: 0.94118
```




    0.9411764705882353



## Exercise 4

Two boxes are filled with black and white balls. In the first box, there are 3 white balls and 7 black ones, in the second box, there are 6 white balls and 4 black ones. Jenna takes one ball out of box 1 and puts it in the second box without looking at the color. then he takes a ball out of the second box and notices that it's white. Now, it's your turn to compute the probability that Jenna put a white ball from the first box into the second. Use bayes formula to do this! It will help if you define events $A, A'$ and $B$.

### Solution

Denote event A the event that Jenna put a white ball from the first box to the second.

Denote event B the event that Jenna draws a white ball from box 2.

$P(A \mid B)= \dfrac{P(A)P(B\mid A)}{P(A)P(B\mid A)+ P(A')P(B\mid A')}$


```python
P_a = 3/10
P_ac = 7/10
P_b_given_a= 7/11
P_b_given_ac= 6/11


p_a_given_b = (P_a*P_b_given_a)/(P_a*P_b_given_a + P_ac*P_b_given_ac  )
p_a_given_b
```




    0.33333333333333337


