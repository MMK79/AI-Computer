[Lecture-01 Link](https://youtu.be/mbyG85GZ0PI?si=_Q3PkS1nyoVFTSN7)
[Playlist Link](https://youtube.com/playlist?list=PLvx5ei9aEEqKgDZ7oaQGSToFi-QER4v1M&si=pcF9L34CxLDyv06l)
## Outline Course:
-   Lecture 1: [**The Learning Problem**](http://www.youtube.com/watch?v=mbyG85GZ0PI&hd=1) (Conceptual)
-   Lecture 2: [**Is Learning Feasible?**](http://www.youtube.com/watch?v=MEG35RDD7RA&hd=1) (Mathematical)
-   Lecture 3: [**The Linear Model I**](http://www.youtube.com/watch?v=FIbVs5GbBlQ&hd=1) (Practical)
-   Lecture 4: [**Error and Noise**](http://www.youtube.com/watch?v=L_0efNkdGMc&hd=1) (Conceptual)
-   Lecture 5: [**Training versus Testing**](http://www.youtube.com/watch?v=SEYAnnLazMU&hd=1) (Mathematical)
-   Lecture 6: [**Theory of Generalization**](http://www.youtube.com/watch?v=6FWRijsmLtE&hd=1) (Mathematical)
-   Lecture 7: [**The VC Dimension**](http://www.youtube.com/watch?v=Dc0sr0kdBVI&hd=1) (Mathematical)
-   Lecture 8: [**Bias-Variance Tradeoff**](http://www.youtube.com/watch?v=zrEyxfl2-a8&hd=1) (Mathematical)
-   Lecture 9: [**The Linear Model II**](http://www.youtube.com/watch?v=qSTHZvN8hzs&hd=1) (Practical)
-   Lecture 10: [**Neural Networks**](http://www.youtube.com/watch?v=Ih5Mr93E-2c&hd=1) (Practical)
-   Lecture 11: [**Overfitting**](http://www.youtube.com/watch?v=EQWr3GGCdzw&hd=1) (Conceptual)
-   Lecture 12: [**Regularization**](http://www.youtube.com/watch?v=I-VfYXzC5ro&hd=1) (Practical)
-   Lecture 13: [**Validation**](http://www.youtube.com/watch?v=o7zzaKd0Lkk&hd=1) (Practical)
-   Lecture 14: [**Support Vector Machines**](http://www.youtube.com/watch?v=eHsErlPJWUU&hd=1)  (Mathematical - Practical)
-   Lecture 15: [**Kernel Methods**](http://www.youtube.com/watch?v=XUj5JbQihlU&hd=1)  (Mathematical - Practical)
-   Lecture 16: [**Radial Basis Functions**](http://www.youtube.com/watch?v=O8CfrnOPtLc&hd=1) (Practical)
-   Lecture 17: [**Three Learning Principles**](http://www.youtube.com/watch?v=EZBUDG12Nr0&hd=1) (Conceptual)
-   Lecture 18: [**Epilogue**](http://www.youtube.com/watch?v=ihLwJPHkMRY&hd=1) (Conceptual)

Machine Learning is a very broad subject, it goes from very abstract theory to extreme as in rules of thumb, and the inclusion of the topics in the course depends on the relevance to machine learning.
**So some mathematics are useful cause they will give you some conceptual framework, and then some practical aspects are useful because they give you the way to deal with real learning system.**

### The story line of the course:
1. What is Learning? (1-7)
2. Can we Learn? (8-9)
3. How to do it? (10-12)
4. How to do it well? (12-16)
5. Take-home lessons (17-18)

There is a logical dependency that goes through the course except one lecture, lecture 3; it is practical topic and the reason that I included early on is because I needed to give you some tools to play around with, to test theoretical and conceptual aspects, it normally belong to the second aspects but if I did it like this the beginning of the course will be very theoretical.

## Lecture 1 Summery:
* Example of Machine Learning: fun example about movies that capture the essence of Machine Learning
* Component of Machine Learning: I'm going to abstract from the learning problem, practical learning problem, aspect that are common to all learning situation that you are going to face. And in abstracting them, we'll have the mathematical formalization of the learning problem. 
* A Simple Model: And then we will get our first algorithm for machine learning today. it is a very simple algorithm but it will fix the idea about what is the role of algorithm in this case. 
* Types of Learning: And then we will survey the types of learning, so that we know which part of we are emphasizing in this course, and which part is nearby.
* Puzzle: it is a puzzle more than in one way

## Example:
**Predicting how viewer will rate a movie?**
It is an interesting problem for us because we watch movies, and very interesting for companies that rent out movies, and indeed the company which is Netflix wanted to improve the in-house system by a mere 10%.
So they make recommendation when you log in, they recommend the movies that they think that you will like, so they think that you'll rate them highly. And they had a system for it and now they want to improve this system.
so how much 10% improvement in performance worth in the company? 1 Million dollar prize!
You may ask why the 10% improvement worth 1 million dollar? It's because the recommendation that the movie makes, are spot on, you will pay more attention to the recommendation, you are likely to rent a movie that they recommend and they will make lots of money, And this is very typically Machine Learning. 
For example machine learning has an application on financial forecasting. you can imagine that the minutest improvement in the financial forecasting can make a lot of money.
**So the fact that you can actually push the system to be better by using machine learning is a very attractive aspect of the technique in a wide spectrum of application.** 
now if you look at the problem it capture the essence of machine learning and the essence has three components. If you find these 3 components in a problem that you have in your field, then you know that the machine learning is ready as an application tool.

### Essence of Machine Learning:
* **A Pattern Exists.**
	if the pattern don't exists, there won't be nothing to look for, but what is the pattern here? There is no question that the way a person rate a movie is related to how they rated other movies, and is also related to how other people rated that movie. So there is a pattern to be discovered. 
* **We cannot really pin it down Mathematically:**
	I cannot ask you to write a 17th-order polynomial that captures how people rating movies.
	So the fact that there is a pattern, and that we cannot pin it down mathematically is the reason that why we are going to use machine learning. For **"Learning From Data"**. We couldn't write the system on our own, so we're going to depend on data in order to be able to find the system.
* **We have data on it.**
	If you don't have this part you are out of luck. We have to have data. We are learning data. <mark style="background: #FF5582A6;">The First question that we need to ask is What data do you have?</mark> 
If you have all these 3 components you are ready to apply machine learning.

#### Solution to movie rating:
<!--![[Movie-rating-solution.png]]-->
![](https://i.imgur.com/0CtUCDW.png)

as you can see in the image above you have a system.
* User:
We are going to describe a viewer as a Vector of Factors, like: does the user like comedy, dose he/she like actions and etc. you can go so deep like do they like specific Actor and go on.
* Movie:
Now you go to the content of the movie itself, and you get the corresponding part, like: does the movie 
have comedy? does it have action and so on.
* Rating:
And then you compare the two, and you realize that if there is a match between so many coordinates you will like the movie and if the is so many mismatch the chance that you don't like the movie is high.
* Summery:
**You match the Movie and the Viewer Factors, and then you Add the Contribution of them , and as a Result of that you get the Predicted rating**
**<mark style="background: #FF5582A6;">This is really not Machine Learning</mark>**
In order to produce this thing, you have to watch the movie and analyze the content. You have to interview the viewer and ask about their taste. And then you combine them and get the prediction for the rating.
The idea of machine learning is that you don't need to do any of that, all you do is to sit down and sip on your tea, <u>while the machine is doing something to come up with this figure on its own.</u>
##### Learning Approach:
<!--![[Learning-approach-01.png]]-->
![](https://i.imgur.com/SPDIbdp.png)

We know that the viewer will be a vector of different factors, and different components for every factor. So this Vector will be different from one Viewer to another. Same will happen for the movies and then the way we computing the rating, is by simply taking these and combining them and getting the rating
Now what <mark style="background: #FF5582A6;">machine learning will do, is Reverse-Engineer that Process</mark>:
	It starts from the rating and then tries to find out what factors would be consistent with that rating.
<!--![[Learning-approach-02.png]]-->
![](https://i.imgur.com/c3DiZP8.png)

You start, let's say, with completely random factors. For each of your movies and viewers you start with random numbers from the beginning to end, this is your Starting Point.
Obviously, there is no chance that in the world that when you get the inner product between these factors that are random, that you'll get anything that looks like the rating that actually took place, right? But What you do is you take the rating that actually happened, and then you start nudging the factors ever so slightly towards that rating, Make the direction of the product closer to the rating.
Now it looks like a hopeless thing: I start with so many factors, they are all random, and I'm trying to match them match rating. What are the chances? Well the point is that you are going to do this not just for one rating, but for a 100 million ratings. And you will cycling through the 100 million, over and over and over. And eventually, lo and behold, you find out that the factors now meaningful in terms of rating.
And if you get a viewer that didn't watch a specific movie but you have his/she vector that you got from the process, and then you get a vector of that specific movie that resulted from the process, and then you do the inner product, lo and behold you get the rating which is actually consistent with how that viewer rates the movie.

## Components of Learning:
So now I would like to abstract from the learning problems that I see, what are the mathematical component that make up the learning problem?
So now I'm going to use metaphor now from another application domain, which is a financial application.
* Metaphor: Credit Approval
you apply for the credit card, and the bank wants to decide whether it's a good idea to extend a credit card for you or not.
from the bank point of view, if they are going to make money they are happy, and if they're going to lose money they are not happy. That is the only criterion they have. There is no magic formula for bank to decide whether a person is creditworthy or not. What they are going to do is to rely on the historical records of previous customers. and how their credit behavior turned out, and then try to reverse-engineer the system and when they get system frozen, they are going to apply it to a future customer.
* Applicant Information:
<!--![[Components-of-learning.png]]-->
![](https://i.imgur.com/s5OiOMh.png)

all kind of field that are believed that are related to creditworthiness. There is no question that these fields are related to the creditworthiness. They don't necessarily uniquely determine it, but they are related. 
And the bank doesn't want a sure bet, they want to get the credit decision as reliable as possible. So they want to use that pattern in order to be able to come up with a good decision. And they will take this input, and they want to approve the credit or deny it. Let's formalize this
* Formalization:
	* Input: $x$ = Customer Application:
	 So we can think of it as a d-dimensional vector, the first component is a salary, and etc. you put them as a vector and that become the input.
	* Output: $y$ = Decision --> extend the credit or not to extend it, +1 and -1.
	* Target Function: $f: X \rightarrow Y$ (Ideal Credit Approval Formula) --> which we don't know
	 the target function is a function from a domain $X$ which is all the $x$'s so it is a set of vectors of d-dimensions. in this case it is d-dimensional Euclidian Distance, and the $Y$ is set of all $y$'s, that in this case is easy cause it is only +1 and -1, accept or deny, And therefore this is just a binary co-domain. 
	 **In all of our endeavors in machine learning, the target function is unknown to us.** if it where known, nobody needs learning. We just go ahead and implement it. but we need to learn it because it is unknown to us. So what are we going to do to learn it? 
	* Data: $(x_{1}, y_{1}), (x_{2}, y_{2}), \dots,(x_{N}, y_{N}) )$ (Historical Records)
	* Hypothesis: $g: X \rightarrow Y$ (Formula to be Used)
	 is the formal name we're going to call the formula we get to approximate the target function. So the hypothesis live in the same world/scope as the target function, and if we look at the value of the $g$ it supposedly approximate the value of $f$.
	** while $f$ is unknown to us the $g$ is very much known/actually we created it and the hope is that it does approximate $f$ well.** That is the goal of learning.
<!--![[Machine Learning/Course/Yaser Abu-Mostafa - Caltech/Lecture-01/Attachments/Learning-Diagram.png]]-->
![](https://i.imgur.com/FLkqotV.png)

* Learning Algorithm is a part that connect the Training Examples and the Hypothesis to each other: it will takes the examples and will produce the final hypothesis
There is an another component that goes into the Learning Algorithm. So what is the learning algorithm does, it creates the formula from a **preset model of formula**, set of candidate formulas if you will. And these what we are going to call **the Hypothesis Sets** which we are going to pick one hypothesis. 

the top part of these chart from the unknown target function to training data to learning algorithm and final hypothesis is **very natural and Nobody will object that**, but why do we have this hypothesis set? why not let algorithm pick from anything? just create the formula without being restricted to a particular set of Formula, there is 2 reason:
1. There is no downside for including a hypothesis set in the formalization.
	the reason is so simple, cause you do the same in <u>practical point of view</u>, that is what you do. And if you don't want to restrict yourself at all, very well, then your set of hypothesis set is the set of all possible hypothesis, so there is **no loss of Generality in putting it.**
2. There is Upside:
 The upside is not obvious here but it will become obvious when we go through the Theory. **The hypothesis set will paly a pivotal role in theory of learning**, it will tell us: can we learn, and how well we learn, and whatnot. Therefore having it as an explicit component in the problem statement will make the theory go through.

### Component of Solution:
What is Solution Component means? <u>The target function is not under your control</u>, <u>I have no Control over historical data too, but you get the data</u>, and <u>you need to hand over the final hypothesis to get your check</u> so all of these parts are dictated.
<u>**The Learning Algorithm** and **The Hypothesis Set** are your solution tools.</u> These are things you choose to solve the problem
* Hypothesis Set: $H = \{h\} g \in H$
	we choose $H$ for the set, and the element $h$ is a function, pretty much like the final hypothesis $g$ and the $g$ is one of them that you happen to elect. So when we elect it we call it $g$ and if it sitting there generically, we call it $h$
* Learning Algorithm: that will do the searching and produce one Hypothesis
<mark style="background: #FF5582A6;">Together, they are referred to as the **Learning Model**</mark>
So if you are asked what is the Learning model that you are using, you're actually choosing both hypothesis set and learning algorithm, like; (Hypothesis set, Learning Algorithm)
(perceptron model, perceptron algorithm), (Neural Network, back propagation), (SVM radial basis function version, quadratic programming)
## Simple Hypothesis set - The Perceptron
<!--![[PLA-02.png]]-->
![](https://i.imgur.com/yrMq8di.png)

<u>it takes attribute you have and gives them a different weights, w.</u> <mark style="background: #FFF3A3A6;">if your attribute is important the chance that are $w$ corresponding to that attribute will be big, and on the opposite side if the attribute is not that important the chances are the $w$ that goes with it is not that big.</mark> 
Now you add them together, and <u>you add them in linear form that's what it makes it perceptron</u>
as you can see in the image above what defines $h$ is your choice of <u>$w_{i}$</u> and <u>threshold</u>. These are the parameters that define one hypothesis versus the other.
$x_{i}$ is an input that will put into any hypothesis. As far as we are concerned when we are learning the inputs and outputs are already determined. These are the Data Sets. 
But what we vary to get one hypothesis or another, and what the algorithm needs to vary in order to choose the final hypothesis, are those parameters.
### Visual Part
#### Hypothesis Set
<!--![[PLA-03.png]]-->
![](https://i.imgur.com/gOdl4ny.png)

let's assume that the data that you are working with is linearly separable. the right image is what you want to achieve in the end of your learning. purple line in both case correspond to the purple parameters $w_{i}$ and threshold, once choice of these 2 will correspond to one line. and when you change them you get another line.
The learning algorithm is playing around with these parameters, and therefore moving the line around, trying to achieve the right image purple line.
now we gonna have simple change in notation, instead of call it "Threshold", we're going to treat it as if it's a weight. it was "- threshold" now we call it "$+ w_{0}$" now just say that $w_{0} = - threshold$ that is it. 
Why we do that?
<u>We do that because we are going to introduce an artificial coordinate $x_{0} = 1$, this is not an attribute, but an artificial constant we add which happens to be always +1. </u>
Why are we doing this?
<u>Because when you do that then all of a sudden the formula simplifies.</u>
And now in the end we put it as a vector form, which will simplify matters, so in this case you will be having the inner product between a vector $w$, a column vector, and vector $x$. 
Now we have the Hypothesis set. let's go for the learning algorithm.
#### Learning Algorithm
Hypothesis set will tells you the resource you can work with. Now we need algorithm that is going to look at the data, and navigates trough the space of hypothesis, to bring the one that is going to output as the final hypothesis that you will give to your customer.
<!--![[PLA-01.png]]-->
![](https://i.imgur.com/6fjs0XI.png)

it takes the training data, that is what is a learning algorithm always does. This is their starting point.
and then What does it do? 
It tries to make $w$ correct, so it really doesn't like when a point is misclassified, so if a point is miss classified it means that your $w$ didn't do the right job here.
What does it mean to be misclassified point here?
It means that when you apply your formula, with the current $w$ apply it to this particular x ($x_{n}$) then what happens, is that you get something that is not $y_n$ you want. 
What do we do when a point is misclassified?
What algorithm does, it updates the weight vector. it changes the weight, which changes the hypothesis, so it behave better on that particular point. 
<!--![[Inner-Product.png]]-->
![](https://i.imgur.com/JVpC5G2.png)

so what is misclassified mean is that their inner product is positive but they should be negative or their inner product is positive but it should be negative.
look at the final formula:
$$\textcolor{red}{w} + y_{n}x_{n} \rightarrow \textcolor{blue}{w}$$
it takes the old $w$ and adds something that depends on the misclassified point. both in terms of $x_n$ and $y_{n}$ while $y_{n}$ is just +1 or -1, so here you are either adding a vector or subtracting a vector.
And you can see from the diagrams on the right part, that you are always doing is such a way that you make a point more likely to be correctly classified.
How is that?
if $y = +1$ as you can see on the top right, then it must be that since the point is already misclassified that $w.x$ was negative. Now when you modify it to $w + yx$ it is actually $w + x$ and when you add $x$ to $w$ you get the blue vector instead of the red vector and lo on behold, now the inner product is indeed positive.
So this is the intuition behind it. However, it is not the intuition that makes this work. There are number of problem with this approach. what we wanted to achieve from this part was that it is not a crazy rule. Whether it is not a working rule, that is yet to be seen.
#### Iteration of Perceptron Learning Algorithm - PLA
<!--![[PLA-Iterations.png]]-->
![](https://i.imgur.com/mDiKB8h.png)

if you do that and the data was originally linearly separable, then you will end up with case that you will get correct solution.
* ! what it says is that it doesn't matter which misclassified data you chose, in the end you will get the right answer that classify all data correctly.
it is not a obvious statement, it requires a proof and the proof is not that hard. But it gives us the the simplest possible learning model we can think of.
It is not clear that the final hypothesis that you hand over to bank is good, because all you did was match the historical records. 
Well you may ask the question: <u>If I match the historical records, does this mean that I'm getting future customers right?</u><mark style="background: #FF5582A6;"> which is the only thing that matters</mark>! The bank already knows what happened with the previous customers. It's just using the data to help you find a good formula. The formula will be good or not good to the extent that applies to a new customer, and predict the behavior correctly. Well, that's a loaded question which will be handle in extreme detail, when we talk about the theory of learning. 
## Types of Learning
* Basic Premise of Learning, which the different type came about.
	* Using a set of observation (Data) to uncover an underlying process (Target Function) --> this is the common premise between any problem that you will consider learning --> this is a broad premise --> so it have so many variation in different sciences --> Statistics --> (in statistics) the underlying process = probability distribution AND the observation = samples that generated by that distribution AND you want to take the samples, and predict what the probability distribution is. 
	* When we talk about different type of learning, it's not like we sit down and look at the world and say, this looks different from this because the assumptions looks different. <mark style="background: #FF5582A6;">What you do is, you take this premise and apply it in context.</mark> And that <u>calls for certain amount of mathematics and algorithms.</u> <mark style="background: #FF5582A6;">If a particular set of assumptions takes you sufficiently far from the mathematics and algorithm you used in other disciplines, that it takes on life of its own. And it develops its own math and algorithm, then you declare it different type.</mark>
### Supervised Learning
<!--![[Supervised-learning.png]]-->
![](https://i.imgur.com/gzPyeAt.png)

Anytime you have the data that given to you, with the output explicitly given, it's as if it a supervisor is helping you out, in order to able to classify the future one. 
### Unsupervised Learning
<!--![[Unsupervised-Learning-01.png]]-->
![](https://i.imgur.com/OkUyONp.png)

Instead of having (input, correct output) we are going to have less information, we just going to have (input), and I'm not going to tell you what a target function is at all.
<!--![[Unsupervised-Learning-02.png]]-->
![](https://i.imgur.com/N1AD6iz.png)

Things tend to cluster together. So I may be able to classify those cluster into categories, without knowing what the categories are. <u>In unsupervised learning the number of clusters is ambiguous at times.</u> 
* A way of getting higher-level representation of the input. 
### Reinforcement Learning
Instead of (input, correct output) we get (input, some output, grade for this output) I am not explicitly giving you the output, but when you choose and output I'm going to tell you how well you are doing. 
<!--![[RL.png]]-->
![](https://i.imgur.com/laqwrTR.png)

you make move and eventually you win or lose, so your propagate back the credit because of the winning/losing according to a very specific and sophisticated formula, into the all the moves that happened. Now you think that this is completely hopeless, because maybe this is not the move that resulted in this, it is another move. But always remember that you are going to do this 100 billion times. 
we have a target function that we cannot model. that covers a lot of territory. I've seen a lot of those. we have the data that coming from the target function.
## Puzzle
<!--![[Learning-Puzzle.png]]-->
![](https://i.imgur.com/qO9a9xs.png)

We don't care if it's a +1 or -1, What we care about is that We getting both answers. that is the essence of this problem.
in reality this is an impossible task, the target function is unknown. and you only have the value of the target function at 6 points and there is so many target functions that the value of them in that 6 point is the same but they behave completely different outside.
we are going to show that the learning is good and alive, without compromising our basic premise. The target function will continue to be unknown, and we still mean unknown, and we will be able to learn. 

## Q&A (since min 57)
* How do you determine if a set of points linearly separable? and what you do if they are not separable? 
The linear separable assumption is a very simplistic assumption, and doesn't apply most in practice. And I chose it only because it goes with very simple algorithm, which is the Perceptron Learning Algorithm. 
There are two ways to deal with the case of linear inseparability: There are algorithms, and most algorithms actually deal with that case, and there's also technique that we are going to study, which will take a set of points which is not separable, and create a mapping that makes them linearly separable.
in general when you get data from someone you assume that it's not generally separable. 
There is a simple modification of the perceptron learning algorithm, which is called the Pocket Algorithm, that applies the same rules with a very minor modification, and deals with the case when the data is not separable. However if you apply the perceptron learning algorithm that is guaranteed to converge to a correct solution in the case of linear separability. 