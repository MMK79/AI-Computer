## [[Lecture-01]] Review
<!--![[Review of Lecture-01.png]]-->
![](https://i.imgur.com/tSgCBHD.png)

### Components of Learning
2 that you can do without and one that absolutely essential, what do I mean? 
let's say you don't have a pattern. Well, if you don't have a pattern, then you can try learning, and the only problem is that you will fail. But the idea here is that, when we develop the theory of learning, we will realize that you can applies the technique regardless of whether there is pattern or not. And you are going to determine whether there is a pattern or not.
So you are not going to be fooled and think, I learned, then give the system to your customer, and then the customer be disappointed. 
There is something that you can actually measure that will tell you whether you learned or not. if there is no pattern there is no harm in trying machine learning.
another thing that you can do without, let's say that we can pin the thing down mathematically. Well, in that case machine learning is not a recommended technique. It will still work, it may not be the optimal technique if you can outright the program it, and find the result perfectly then why bother generate examples and try to learn, and go through all of that? but machine learning is not going to refuse, it is going to learn, and it is going to give you system. It may not be the best system in this case, but it's a system nonetheless.
**You have to have Data.** Machine learning is about learning from data. And if you don't have data, there is absolutely nothing you can do.
### Supervised Learning
Unknown is very generous assumption, which means that you don't have to worry what pattern you are trying to learn. it could be anything and you will be learn it.
it is a good assumption you have, because then you know you don't have to worry about the environment that generate the examples, you only worry about the system that you use to implement machine learning.
So in spite the fact that the target function is generally unknown, it is known on the data that I give you. This is the data that you are going to use as training examples, and that you are going to use to figure out what the target function is.
## Is Learning Feasible?
* Probability to the rescue
Start with probabilistic situation, that is very simple, and it doesn't seem to relate to learning, but it will capture the idea, can we say something outside the sample data that we have? so we gonna answer it in a way that is concert and the mathematic is very friendly
* Connection to learning
then we are going to relate that probabilistic situation, in first part we just sort of translate the expression into something that relates to learning
* Connection to real learning
and then we will move forward and make it correspond to real learning 
* A dilemma and a solution
In the end we will find out that there is a serious dilemma that we have, and we will find a solution to that dilemma and declare the victory, indeed learning is feasible in a particular sense.

## A Related Experiment
- You have a "bin" with <span style="color: red;">red</span> and <span style="color: green;">green</span> marbles. 
<!--![[Related-experiment-01.png]]-->
![](https://i.imgur.com/iCN2NeZ.png)

we are going to do experiment with this bin, and the experiment is to pick a samples from bin. 
$$\mathbb P [picking\ a \ \textcolor{red}{red}\ marble] = \mu$$
$\mu$ is the probability of picking the <span style="color: red;">red</span> marble, now that we know the probability for picking the <span style="color: red;">red</span> marble we want to calculate the probability of $\textcolor{green}{green}$ marble and the result will be:
$$\mathbb P [picking\ a \ \textcolor{green}{green}\ marble] = 1 - \mu$$
* The value of the $\mu$ is unknown to us. (Target Function)(Unknown Constant)
* We pick $N$ marbles independently. (number of Data Points in learning) 
* We call the fraction of <span style="color: red;">red</span> marbles in a sample $\nu$ it is (this is now a probabilistic quantity) 
<!--![[Related-experiment-05.png]]-->
![](https://i.imgur.com/7dTvNk9.png)

as you can see in the image $\nu$ should also appear in the figure, in the empty place that you have before the = sign in the image but for some reason that we don't understand $\nu$ doesn't show itself in the figure, so we decide maybe the app is the machine learning expert, it doesn't like things in sample, it only like things that is real. 
So it knows that $\nu$ is not important, and it's not an Indication, we are really interested in knowing what is outside, so it will keep the $\mu$ and deleted the $\nu$.
now there is a important question that we asked in machine learning:
### Does $\nu$ (Sample frequency) say anything about $\mu$ (Actual Frequency) ?
The short answer:
* No!
Because the sample can be mostly <span style="color: green">green</span> while the bin is mostly <span style="color: red">red</span> (we can have a bin with 90% red marbles and when you pick samples they happened to be all green, This is <mark style="background: #FF5582A6;">Possible!</mark> but the chance to this even happen is very low)
The Long answer:
* Yes!
If the samples is big enough the Sample Frequency $\nu$ is likely close to Actual Frequency $\mu$ (Bin Frequency)

The <u>Main distinction</u> between two answers is: **Possible Vs. Probable**
In science and engineering, you go a huge distance by settling for not absolutely certain, but almost certain. It opens the world of possibilities, and one of the possibilities that it opens.
from probabilistic point of view $\nu$ does tell me something about $\mu$
### What <u>does</u> $\nu$ say about $\mu$?
* In a big sample (large $N$), $\nu$ is probably close to $\mu$ (within $\epsilon$)
Formally:
$$\mathbb P[\ \ \ \ \ \ \ \ \ \ \ ] \le \ \ \ \ \ \ \      $$
We are going to say that the probability of something is small. So we're going to say that it's less than or equal to, and hopefully the right-hand side will be a small quantity.
now if I'm claiming that the probability of something is small, it most be that thing is bad event. I don't want it to happen. 
So we have a probability of something bad happening being small.
$$\mathbb P[Bad \ Event] \le \ \ \ \ \ \ \      $$
what is the bad event in the context of what we are talking about? $\nu$ doesn't approximate $\mu$ well
$$\mathbb P[|\nu - \mu| > \epsilon] \le \ $$
this is bad because that tells us that they are further away from our tolerance epsilon. We don't want this to happen. + We would like that the probability of that happening to be small as possible.
Well, how small can we guarantee it?
$$\mathbb P[|\nu - \mu| > \epsilon] \le e^{-N}$$
Good news! it is $e^{-N}$, it's negative exponential. That is great because negative exponential tend to die very fast. So if you get bigger samples this will be diminishingly small probability. 
So the probability of something bad happen is very small, and we can claim that, indeed, $\nu$ will be within $\epsilon$ from $\mu$, and we will be wrong for a very minute amount of the time. 
But What is the Bad News?!
$$\mathbb P[|\nu - \mu| > \epsilon] \le e^ {-\epsilon^{2}N}$$
Epsilon is our tolerance, if you are a very tolerant person, you say: I just want to $\nu$ and $\mu$ be within the 0.1. Now you price for that is that you in the exponent, not $\epsilon$ but $\epsilon^{2}$ so now the 0.01 will dampen N significantly, and you lose a lot of benefit of the negative exponential. 
the final formula is:
$$\mathbb P[|\nu - \mu| > \epsilon] \le 2e^ {-2\epsilon^{2}N}$$
the formula with the 2's has a distinct advantage of being: True
This is what we call Hoeffding's Inequality
In the other word, the statement $\mu = \nu$ is P.A.C (probably, approximately, correct)
* Probability because of $-2\epsilon^{2}N$
* Approximately because of $\epsilon$
One attraction of this inequality is that it is valid for every $\mathbb N$, positive integer, and every $\epsilon$, greater than zero. --> pick any tolerance you want, and for any number of example this inequality is true. --> it is not an asymptotic result! It is a result that holds for every N and epsilon --> this is attractive proposition for something that has the exponential in it.
Hoeffding's Inequality belongs to a large class of mathematical laws, which are called the Laws of Large Number. This happen to be the friendliest because it have exponential in it and it's not a asymptotic.
Now if you look at the left-hand side , we are computing $\mathbb P[|\nu - \mu| < \epsilon]$ this probability, and this probability patently depends on $\mu$, $\mu$ appears explicitly in it, and also $\mu$ affect the probability distribution of $\nu$, $\nu$ is the sample, in $N$ marbles that you picked. That's a very simple binomial distribution. 
you can find the probability that $\nu$ equals anything based on the value of $\mu$, so the probability that this quantity, which depends on $\mu$, exceeds epsilon. The probability itself does depend on $\mu$. 
However we are not interested in the exact probability, We just want to bound it. And in this case we are bounding it uniformly. 
As you see the right-hand side doesn't have $\mu$ in it, and that gave us great tool, because now we don't use the quantity that, we are already declared, is unknown. 
$\mu$ is unknown, so it would be a vicious cycle if I go and say that it depends on $\mu$, but I don't the $\mu$ is. Now you know uniformly, regardless of the value of $\mu$, $\mu$ could be anything between 0 and 1, and we still be bounding the deviation of the sample frequency from the real frequency.
<!--![[Hoeffding-inequality.png]]-->
![](https://i.imgur.com/PEpuzh1.png)

the $N$ is the number of data, and it is dictated to you --> you can't do anything about it
on the other hand you have $\epsilon$ that is taste of your tolerance. --> you can pick it to be high or low
Now because they get multiplied here --> the smaller $\epsilon$ is, the bigger the $N$ you need to compensate for it and come up with the same level of probability bound. --> if you have more examples, you are more sure that $\nu$ and $\mu$ will be close together, closer, closer as you get larger $N$

While you say that the $\nu \approx \mu$ this implies that $\mu \approx \nu$ to put it simply:
$$\nu \approx \mu \implies \mu \approx \nu$$
the logic here is a little bit subtle. Obviously, the statement is tautology, but I'm just making logical point here.
when you run the experiment you don't know what the $\mu$ is, $\mu$ is unknown AND constant. The only random fellow in this entire operation is $\nu$, that is what the probability is with respect to. You generate different samples and you compute the probability. ($\nu$ is the probabilistic thing and the $\mu$ is the happy constant sitting there, albeit unknown)
Now, the way that you using the inequality is to infer $\mu$, the sample is from $\nu$, that is not the cause and effect that actually takes place. The cause and effect is that $\mu$ effects $\nu$ not the other ways around. But we are using it other way around.
Lucky for us, the form of the probability is symmetric. Therefore, instead of saying that $\nu$ tends to be close to $\mu$, which will be the accurate logical statement. --> $\mu$ is there, and the $\nu$ has the tendency to be close to it.
We instead of that say that, I already know $\nu$, and now the $\mu$ tends to be close to $\nu$. --> we are using this logic.
## Connect to Learning Problem
In the Bin the Unknown is a number $\mu$ but in the Learning problem the Unknown quantity is full-fledged function --> how can we map this 2 problem? The bin problem is so Simplistic! 
<!--![[Learning-connection-02.png]]-->
![](https://i.imgur.com/s4WkKJe.png)

now we want to give the colors to the marbles:
<!--![[Learning-connection-03.png]]-->
![](https://i.imgur.com/bVGOVzC.png)

what does green marbles correspond to in learning problem? they are correspond, to your Hypothesis getting it right. What does it mean? There is a target function sitting there, you have hypothesis, and this hypothesis is a full function like the target function is. you can compare the target function and the hypothesis function in every point. And they either agree or disagree. if they agree please color the corresponding point green.
Now we are not saying you know which one is green and which ones are not, because you don't know the target function overall. this is the mapping process that takes the unknown target function into the unknown $\mu$. 
<!--![[Learning-connection-04.png]]-->
![](https://i.imgur.com/Gwk4QXp.png)

now we are just collapsing the whole thing into just agreement, disagreement between your hypothesis and the target function, and that's how you get the colors like the colors of the bin. 
<!--![[Learning-connection-05.png]]-->
![](https://i.imgur.com/RMsZXcy.png)

Now, this will add a component to learning problem that we did not have before. There is a probability associated with the bin, when we talked about the learning problem there was no probability! we just had a sample set and all we needed to do was to work with them. 
So let's see what is the addition we need to do in order to adjust the statement of learning problem to accommodate the new ingredient. And the new ingredient is important, because otherwise we cannot learn. It is not we have the luxury to doing anything without it.
<!--![[Courses/Yaser Abu-Mostafa - Caltech/Lecture-02/Attachments/Learning-diagram.png]]-->
![](https://i.imgur.com/tSIg8jm.png)

in the bin analogy we had a input space that include the probability, so we need to apply this probability to the point from the input space that being generated. So we are going to introduce the probability distribution over the input space. --> so now the point in the input space, are not just generic points now, there is a probability of picking one point versus the other. --> which will be capture by the probability which we are going to call the $P$.
1. The interesting part is that we are making no assumption about the $P$, it can be anything but we just need some sort of probability. --> So invoke any probability that you want, and I am ready with the machinery. --> we are not going to restrict the probability distribution over the $X$
2. We don't even need to know what $P$ is. Of course the probability choice will affect the choice of the probability of getting a green/red marble, because now the probability of different marbles change, so it could change the value of $\mu$
The good news with Hoefding is that I could bound the performance independently of $\mu$. So I can getaway with not only any $P$, but with a $P$ that I don't know, and I'll still be able to make a mathematical statement.
So this is a very benign addition to the problem. And it will give us very high dividends, which is the feasibility of learning.
So what do you do with the probability? You use the probability to generate the points $x_{1} \dots x_{N}$, so now the $x_{1} \dots x_{N}$ are assumed to be generated by that probability independently. --> this is the only assumption that is made.
good news is that we are not making any assumption about the target function that is unknown, and the new addition is almost technical. --> that there is a probability somewhere, generating points. --> if I know that, then I can make statement in probability. --> Obviously, you can make that statement only to the extent that the assumption is valid. --> we will discuss it in the future lectures. 
### Are we done?
Not so fast! Because the analogy that lead us to this place requires a particular hypothesis in mind. the color of the marbles is corresponding to agreement/disagreement between Your Hypothesis function and the Target function ---> What is the problem with this? --> The problem is that I know that for this $h$, $\nu$ generalize to $\mu$ --> yeah, $h$ can be anything so what is the problem? --> The problem is that, what we discussed is not learning, it's verification. --> So instead of actually taking the data and searching hypothesis, and picking one, like perceptron algorithm, here is what we do that correspond to what we described till now; Sitting down, improvising an $h$ --> now after fixing the $h$, I ask you for the data and just verify whether the $h$ is good or bad. --> with the bin logic you can definitely do it like this, because I am going to look at the data, and if I miraculously agree with everything in your data, I can definitely declare victory by Hoeffding. --> what are the chances that this happens in the first place? 
I have no control over whether I will be good on data or not. --> The whole idea of learning is that we are searching the space to deliberately find the hypothesis that work well on the data. --> In this case we just dictated the hypothesis, and we are able to tell you for sure what happens out-of-sample and you develop the system base on that but when you apply it to real data you get the terrible result.
<!--![[Verification-not-learning.png]]-->
![](https://i.imgur.com/9kI464B.png)

what it means when you say you chose the hypothesis from the multiple $h$'s?
In this case you are going to go for the sample, so to speak, generated by every hypothesis, and then  you pick the hypothesis that is most favorable, that gives you the least error. 
It worked with one bin, so maybe I can have more than one bin, to accommodate the situation where I have more than one hypothesis.
<!--![[Multiple-bins.png]]-->
![](https://i.imgur.com/qUrCN9v.png)

I have the samples, and the samples here are different. And I can do the learning, and the learning now, abstractly, is to scan these samples, looking for a good sample. And when you find the good sample, you declare victory because of Hoeffding, and you say that it must be that the corresponding bin is good, and the corresponding bin is happen to be the hypothesis you chose. so this is the abstraction of learning.
## Notation for Learning
<!--![[Learning-Notation.png]]-->
![](https://i.imgur.com/3IHbkYd.png)

<!--![[Multiple-bins-notation.png]]-->
![](https://i.imgur.com/whwkLUW.png)

Are we done? Nah! The Hoeffding doesn't apply to multiple bins
## Coin Analogy
<!--![[Coin-analogy.png]]-->
![](https://i.imgur.com/i68aMd4.png)

<!--![[Convert-coin-to-learning.png]]-->
![](https://i.imgur.com/ZSLL0xI.png)


Hoeffding Inequality, if you have one experiment it has a  guarantee, the guarantee get terribly diluted as you go, and we want to know exactly how the dilution goes. 
## Simple Solution
Union Bound it is a very loose bound in general, because it doesn't consider the overlap.
<!--![[Simple-solution-01.png]]-->
![](https://i.imgur.com/oqzcf5V.png)

if you are very unlucky and these are non-overlapping, they add up. The non-overlapping is the worst-case assumption, and it is the assumption used by the union bound.
The good news is that we have a handle on each term of them. the union bound is coming up. So we put the OR's 
<!--![[Simple-solution-02.png]]-->
![](https://i.imgur.com/63BQAvp.png)

each term here is a fixed hypothesis, we didn't choose anything. Everyone of them has a hypothesis that was declared ahead of time. Everyone of them is a bin. 
<!--![[Final-verdict.png]]-->
![](https://i.imgur.com/cgiU7Gc.png)

<!--![[Final-verdict-M.png]]-->
![](https://i.imgur.com/ZUR5lJA.png)

now with M, you realize that OK, if you use 10 hypothesis, this probability is probably tight. If you use million hypothesis, we probably are already in trouble. There is no guarantee, because not the millions get multiply by what used to be a respectable probability, which is 1 in 100,000 and now you can make the statement that the probability of something bad happen is less than 10, and the problem is extremely intuitive.
The assertion that if you have a more sophisticated model, the chances are you will memorize in-sample, and you are not going to really generalize well out-of-sample because you have so many parameters to work with.
If you pick a very sophisticated example with a large M, you lose the link between in-sample and out-of-sample. the in-sample is supposed to track the out-of-sample. the more sophisticated the model you use, the looser that in-simple will track the out-of-sample. Because the probability of them deviating become bigger and bigger and that is the exactly intuition we have. 
## Q&A (Start from Min 57)
