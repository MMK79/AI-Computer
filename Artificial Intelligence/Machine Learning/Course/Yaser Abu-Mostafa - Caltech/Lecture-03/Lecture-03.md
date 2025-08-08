## Lecture 02 Review
<!--![[Review-Lecture-02.png]]-->
![](https://i.imgur.com/cAWL5hD.png)

Learning is feasible, but only in a probabilistic sense --> we modeled that in terms of a bin --> that has the out of sample performance $E_{out}(h)$, $h$ is the hypothesis that correspond with that particular bin, then we look at the in-sample $E_{in}(h)$ --> with Hoeffding the $E_{in}$ track $E_{out}$, you have tolerance $\epsilon$, and this tolerance have impact on the other side that is the negative exponential power $N$ --> which bigger sample your $E_{in}$ in more reliable
--> this apply to single bin only, and single bin correspond to a single hypothesis --> in full model $h_{1}, h_{2} \dots h_{M}$ , what would apply in this case? 
the problem with having multiple hypothesis is that probability of something bad happen could accumulate. Because if there is a 0.5% chance that the fist hypothesis is bad, in the sense of bad generalization, and 0.5% for the second one, we could be so unlucky that all of these 0.5% accumulate, and end up with a significant probability that one of the hypothesis will be bad, and if on of the hypothesis will be bad, and we further unlucky, and we pick this hypothesis as the final hypothesis, then $E_{in}$ will not track $E_{out}$ for the hypothesis we picked.
So we need to accommodate the case where we have multiple hypothesis, and the argument is very simple $g$ is our notation for the final hypothesis it is one of these guys that the algorithm will chose, well the probability that the $E_{in}(g)$ doesn't track $E_{out}(g)$ will obviously be included in fact $E_{in}(h_{1})$ doesn't track $E_{out}(h_{1})$ and etc. till $E_{in}(h_{M})$ doesn't track $E_{out}(h_M)$, and the reason for this is very simple.
$g$ is one of these guys ($h_{1}, h_{2} \dots h_{M}$), if something bad happens with g, it must happen with one of these guys <u>at least</u>, the one that we happen to pick. so we can say that $E_{in}(g) - E_{out}(g)$ implies these things --> simple mathematical rule, which is Union Bound --> The probability of an event or another event or another event is at most the sum of the probabilities. --> this rules applies regardless of the correlation between these events. because it takes the worst case scenario. If all the bad events happen disjointedly then you add up the probabilities. if there is some correlation, and they overlap, you get the smaller number.
**In all of the cases, the probability of $|E_{in}(g) - E_{out}(g)| > \epsilon$ will be less than or equal to sum of the individual probabilities**
in the case of hypothesis of a model, the events might not be independent, because we have the same sample and we are only changing the hypothesis, so it could be that the deviation between hypothesis related to each other but the Union Bound doesn't care about this, regardless of such correlation you will be able to get the bound on the probability of this event. And therefore you will be able to bound the probability that you care about, which has to do with generalization.
And since you had the $M$ of those, you added the $M$ factor to your formula --> now there is a new problem, because if you use a bigger hypothesis set, $M$ will be bigger and therefore the right-hand side of your inequality bigger, and at some point it even become meaningless --> keep this in mind that we are not even talking about when the $M$ could be infinity which in many cases it is. which make this inequality meaningless.
However we weren't stablishing the final result in learning, we were stablishing **the principal that, through learning, you can generalize.** And we have stablish that. --> in these series of lecture we want to get the ability to say that general learning model, an infinite one, will generalize. and we will get the bound on generalization. The Theory of Generalization.

## Linear Model
the Linear model is **one of the most important** learning model in machine learning.
* Input representation:
practical data set
* Linear Classification
taking perceptron and generalize it through non-separable data
* Linear Regression
generalize it further where the target function is not a binary classification function, but a real-valued function. **one of the most important technique** that is applied mostly in static and economics, and also in machine learning
* Nonlinear Transformation
generalize it to non-linear case, the nonlinear transformation will remain in the realm of linear models 

## Real Data Set
[MNIST Dataset](https://www.kaggle.com/datasets/hojjatk/mnist-dataset/) 
## Input Representation
the raw input, 16 pixels by 16 pixels, so there are 256 real number in that input. so if you look at the raw input x it will be $x = (x_{1},x_{2},\dots, x_{256})$ , very long input to encode such a simple subject. And we add our mandatory $x_{0}$, remember in linear models we have this constant coordinate, $x_{0} = 1$ in order to take care of threshold. So it will always be in background whether we mention it or not.
so if you take this raw input and try the perceptron directly on it, you realize that the linear model in this case, which has bunch of parameters has really just too many parameters.
$$linear\ model: (w_{0}, w_{1}, \dots ,w_{256})$$
if you are working in a 257 dimensional space, that is a huge space. And the poor algorithm is trying to simultaneously determine the value all of these $w$'s base on your set. So the idea of the input representation is to simplify the algorithm's life.
We know something about the problem, we know that it's not really the individual pixels that matter, whatnot You can probably extract some features from the input, and then give those to the learning algorithm, and then let the algorithm figure out the pattern.
### Features
What are features? well, you **extract useful information**, and as a suggestion, very simple one, let's say that in this particular case, instead of giving the raw input with all of the pixels values, you extract some descriptors of what the image is like.
For instance, you look at this. depending on what digit it is, there is a question of the intensity, the average intensity. 1 doesn't have too many black pixels, 8 has a lot, 5 has some. So <u>if you simply add up all the intensity of all the pixels, you probably get a number that is related to the identity</u>. <u>It doesn't uniquely determine it, but it's related.</u> **It's a higher level representation of the raw information.** 
same as symmetry, if you think of the digit 1, 1 will be symmetric. if you flip it upside down or you flip it right and left, you will get the something that overlap significantly with it. So you can also define a <u>**Symmetry measure**, which means that you take the symmetric difference between something and its flipped versions</u>, and you see what you get. if something is symmetric, things will cancel because it's symmetric, and you will get a small value, and if something is not symmetric you will get high value for that. So what you measuring is anti-symmetry, you take the negative of that, and you get the symmetry. 
$$intensity\ and \ symmetry\ x = (x_{0}, x_{1}, x_{2})$$
Now <u>admittedly you lost information in that process</u>. **But the chances are you lost as much as irrelevant information as relevant information.** 
So this is a pretty good representation of the input, as far as the learning algorithm is concerned, and you went from 257 dimensional to 3 dimensional.
you probably realize that having 257 parameters is too bad news for generalization, if you extrapolate from what we said. 
<!--![[Input-representation.png]]-->
![](https://i.imgur.com/9J3txEe.png)

<!--When you take the linear model in--> this case, you just have $w_{0}, w_{1}, w_{2}$, and that's what the perceptron algorithm needs to determine. 
### Illustration of features 
![[Illustration-of-features.png]]
![](https://i.imgur.com/Qq2iAp2.png)

(think of the x-axes as the intensity and the y-axes as the symmetry)
This is a scatter diagram. Every point here is a data point, so it is one of the digits, one of the images that you have. And in this case we are just distinguishing the 1's from the 5's, and you can always take other digits versus each other, and then combine the decision so if you can solve this unit problem, you can generalize it to the other problems.
As you can see in the diagram the intensity of the 5, is usually more than the intensity in the 1. There are more pixels occupied by the 5's than the 1's. the 5's data are tilted a little bit more to the right, corresponding to the intensity.
if you look at the other coordinate, which is symmetry, the 1 is often more symmetric than the 5. and as you can see in the diagram tend to be more higher on the vertical coordinate. 
And just by these two coordinates, you already see that this is almost linearly separable. Not quite, but it is separable enough that if you pass a imaginary boundary line in the diagram, you will get most of them right.
Now you realize that it's impossible really to ask to get all of them right. So we have to accept the fact that there will be stuff that is completely undoable. And we will accept the error, it's not a zero error, but hopefully it's a small error. 
## What does a PLA(Perceptron Learning Algorithm) do?
what it does is this complicated figure, which takes the evolution of $E_{in}$ and $E_{out}$ as a function of iteration.
When you apply the Perceptron learning algorithm, you only apply it on the $E_{in}$. $E_{in}$ is the only value you have. $E_{out}$ is just sitting out there, we don't know what it is, We just hope that $E_{in}$ track it well. 
<!--![[What-PLS-does.png]]-->
![](https://i.imgur.com/jJuxZhM.png)

the x-axes is the iteration numbers, so $x = 0$ is the first misclassified example. You go and apply the perceptron learning algorithm again, again and again. 
as you do that $E_{in}$ which is the $\textcolor{green}{green\ curve}$ will go down, and sometimes will go up. We realize that the perceptron learning algorithms take care of one point at a time, and therefore may mess up the other points while it's taking care of that one point. So in general it can go up or down.
But the bad news is that the data is not linearly separable. And we made the remark that the PLA behaves very badly when the data is not linearly separable. it can go from something pretty good to something pretty bad in one iteration. So what you see is the typical behavior of PLA. Because the data is not linearly separable, the PLA will never converge, so what do we do? We **Force it to terminate** at iteration 1000. We will stop at 1000 and take whatever $\mathbf w$ vector we have, and we call this $g$, the final hypothesis of the PLA.
Now we obviously look at this, and we say, if we took the lowest $E_{in}$ and you say that I will took this guy, this is the better guy than the other, but you know, you're just applying the algorithm and cut it off. 
Now one of the things that you observe here is that, we plotted $E_{out}$. You are not going to be able to plot $E_{out}$ in a real problem that you deal with, if $E_{out}$ is really an unknown function. you may be estimate it using some examples. But all you need to know is that the $E_{out}$ is drawn here for illustration, just tell you what is happening in reality as you work on in-sample error. And in this case you find out that the $E_{out}$ track the $E_{in}$ pretty well. there is a epsilon, but the good thing is that it tracks it down.(when $E_{in}$ goes down the $E_{out}$ goes down and follow it, same happen when the $E_{in}$ goes up.) --> so if your make your decision based on $E_{in}$, the decision base on $E_{out}$ will also be good. --> this is good for generalization. + this is one of the advantageous of something as Perceptron Learning Algorithm. --> It doesn't have too many parameters. And because of our efforts in getting only three features, it even has three parameters now, so the chances are that it will generalize well is high, which as you can see it does.
Now what does the final boundary look like? All you seen till now was only the illustration, now this is the evolution. Eventually you end up with a hypothesis. They hypothesis will separate the points in scatter diagram you saw. So what does it look like? 
<!--![[Final-perceptron-boundary.png]]-->
![](https://i.imgur.com/SKQ27JC.png)

The Bold Black Line is your boundary, this is the final hypothesis, that correspond to the hypothesis you got at the final iteration. Well, it is okay, but definitely not good, it is too deep in the blue region, you could have it lower and had a better result, and the chances are maybe earlier guy that had the better in-sample error will do that. But this is what you have to live with, if you apply the PLA.
Now we are going to modify the PLA in a simple way, the simplest modification you can ever imagine.
### The Pocket Algorithm
<!--![[Pocket-algorithm-01.png]]-->
![](https://i.imgur.com/FPi4UkW.png)

As you can see in the image above, this is what PLA does, and on the red dot you wished, that you could only keep that value. --> Well, this value is not a mystery + it happened in your algorithm. + you can measure it explicitly. + it's an in-sample error. + and you know that it is better than the value that you ended up with. 
So in spite the fact that you are doing these iteration according to the prescribed PLA rule -- modify the weights according to one misclassified point -- you can keep track of total in-sample error of the intermediate hypothesis you got. And only keep the guy that happens to be the best throughout. So you're going to continuing as if it's really PLA, but when you at the end, you keep the best guy and report it as final.
Now the reason that the algorithm is called the Pocket Algorithm is because the whole idea is to put the best solution so far in your pocket. And when you get a better one, you take the better one and put it in your pocket, and throw the old one. And when you are done report the guy in your pocket. 
<!--![[Pocket-algorithm-02.png]]-->
![](https://i.imgur.com/uVVO1TA.png)

Now when you do things like this, you can use PLA with non-separable data, terminate it by force at some iteration, and report the pocket the value. 
<!--![[PLA-vs-Pocket.png]]-->
![](https://i.imgur.com/2qkTBKr.png)

So with this very simple algorithm you can actually deal with general in-separable data, the inseparable data that is basically separable, but you have some bad points that ruins it
## Linear Regression
$Regression \equiv real-value\ output$ There is absolutely no other connotation to it. It's a glorified way of saying my output is real-valued. And it comes from earlier work in statistic, and there is so much work on it that people could not get rid of that term. And it is no a standard term, whenever you have real-valued function, you call it regression problem. 
Linear regression is used incredibly often in statistics and economics. Every time you says: are these variable related to that variable, the first things that come to mind is linear regression. 
<!--![[Linear-regression-credit-metaphor.png]]-->
![](https://i.imgur.com/d7cXZbR.png)

It is regression because the output is real. It's linear regression because the form, in terms of the output, is linear.
Now signal here will play a very important role in all the linear algorithm. this is what the algorithms linear. and whether you leave it alone as a linear regression, you take a hard threshold as a classification or, as we see late you can take a soft threshold, and you get probability, and all of that, all of these are considers linear models.
$$h(x) = \sum_{i=0}^{d} w_{i}x_{i} = \mathbf w^{t}\mathbf x$$
and the algorithm depends on this particular part, which is the signal being linear.
* if you try to minimize the calculus part you can minimize it with respect to scalar variable, which apply very primitive calculus. 
but we are going to work with the shorthand version, which is the vector or the matrix form, in order to be able derivation in easier way. 
<!--![[Credit-data-set.png]]-->
![](https://i.imgur.com/sPRfsw7.png)

This is the statement of the problem, so What does linear regression do?
### How to Measure the Error
We didn't talk about that in the case of classification because it was so simple, but here it's a little bit less simple. now what do we mean by that?
you will have a algorithm that tries to find the optimal weights. and these weights are going to determine what hypothesis you will get. Some of the hypothesis will approximate the $f(x)$ well, and some of them will not.
We want to quantify that, to give us a guidance to the algorithm in order to move from one hypothesis to another. so we will define an error measure, and the algorithm will try to minimize the error measure by moving from one hypothesis to the next.
The standard Error Function in Linear Regression is Squared Error. $(h(x)- f(x))^2$
Well, if you had a classification, there is a simple agreement on a particular example, you either got it right, or got it wrong. There is nothing else. --> Therefore, in that case we just defined the binary error.
Square Error doesn't have and inherit merit here. It just happen to be the standard error function to used with linear regression. and its merit really is the simplicity in the analytic solution that we are going to get. we will discuss error measure in the next lecture, we will get back to this.
<!--![[measure-error.png]]-->
![](https://i.imgur.com/pXuZl2e.png)

So when you look at the in-sample error, you use the error measure. so on the particular example $n \in {1, N}$ , that as you can see they all we affect by the same $w$, because $h$ depends on $w$. So as you change $w$ the value in the parenthesis will change, and this value will change for every example, so if you want to get all the examples error, you simply take the average of those. So this will give you a snapshot of how well your hypothesis is doing on the data. 
And now we are going to ask our algorithm to take this error and minimize it. 
### illustration
<!--![[linear-regression-illustration-01.png]]-->
![](https://i.imgur.com/lnpCxG0.png)

What linear regression does is it tries to produce a line, that tries to fit this data accordingly to the square-error rule. 
<!--![[linear-regression-illustration-02.png]]-->
![](https://i.imgur.com/XUQdiNk.png)

which the threshold depends on the $w_{0}$ and the slope depends on $w_{1}$ which is the weight of $x$, and that is the solution you have. 
<!--![[linear-regression-illustration-03.png]]-->
![](https://i.imgur.com/ZiIBEul.png)

Now you didn't get it right, but what you get is some errors. and if you add of this red lines square to each other you will find the final error
<!--![[linear-regression-illustration-04.png]]-->
![](https://i.imgur.com/oyxCfhv.png)

as you can see you can even apply it to more than one dimension, now in this case the linear thing is really a plane. and when you go higher you will use hyperplanes to do it. 
### Expression for $E_{in}$
That is an analytic expression we going to try minimize, and that will make us derive the linear regression algorithm. 
$$E_{in}(w) = \frac {1}{N} \sum_{n=1}^{N} (h(x_{n}) - y_{n})^2 $$
now because it is linear regression, it happens that the $h(x_n)$
$$E_{in}(w) = \frac {1}{N} \sum_{n=1}^{N} (\mathbf w^{t}\textcolor{blue}{x_{n}} - \textcolor{red}{y_{n}})^2$$
Now if we try to write this in vector form it will become like: 
$$\frac {1}{N} \Vert \textcolor{blue}{\mathbf X} \mathbf w - \textcolor{red}{\mathbf y} \Vert ^2$$
instead of summation, all of a sudden I have a norm squared of something. Well it is a basically a consolidation of different $x_{n}$'s + $x_{n}$ is a vector, so you put a vector in a matrix and call it $\mathbf X$, and you put the scalars, the $y_{n}$ in a vector and call it $\mathbf y$ 
<!--![[In-sample-error.png]]-->
![](https://i.imgur.com/2fmoCk7.png)

the norm square will be simply this vector transpose times itself. And when you do it you realize that what you are doing is summing up contribution from the different components, And each component happens to be exactly what you are having in the $(\mathbf w^{t}\textcolor{blue}{x_{n}} - \textcolor{red}{y_{n}})^2$, so this last one will becomes the shorthand to write the expression.

$$\mathbf x_{1} = \begin{bmatrix} x_{11} & x_{12} & \dots & x_{1M} \end{bmatrix} \underset{1 \times M}{} $$
### Minimizing $E_{in}$ 
when you look at the minimizing, you realize that the matrix $\mathbf X$, which has the inputs of the data, and the $y$ which has the outputs of the data are as far as we are concerned, constants. This is the data set that someone gave me. the parameter that I am actually playing with to get a good hypothesis is $w$
$$E_{in}(\textcolor{purple}{w}) = \frac {1}{N} \Vert \mathbf X \textcolor{purple}{\mathbf w} - \mathbf y\Vert^2 $$
The rest of constant, If I do any calculus of minimization it is with respect to $w$, so when you try to minimize this:
$$\nabla E_{in}(w) = \frac {2}{N}\mathbf X^{T}(\mathbf X \mathbf w - \mathbf y)$$
>[!question]
>You get the derivative and equate it with 0, except here it is a glorified derivative. You get the gradient, which is a derivative on bunch of all of them at once. 
By the way if you hate this and you want to make sure, because the linear regression is so important. And you want to verify that it's true, you can always go for the scalar form, partial E partial every w, get a formula that is pretty hairy one, and then try to reduce it. and solution here you will get a matrix that we have here in two step.
Now if you look at this, deal with it in term of calculus as if it was just a simple square. if this was a simple square, and w was the variable, what would derivative be?


you will get the 2 out side $\frac {2}{N}$ and then you will get the same thing in a linear form $\mathbf X \mathbf w - \mathbf y$, and then you will get whatever constant was multiplied by w to sit outside $\mathbf X^{T}$ you just got it here with a transpose, because this is not really a simple square, this is the transpose of this times itself, and that is where you get the transpose.
And then you equate this to zero, but it is a fat 0, it's a vector of zeros, you want all derivative to be zero all at once. 
$$\nabla E_{in}(w) = \frac {2}{N}\mathbf X^{T}(\mathbf X \mathbf w - \mathbf y) = 0$$
and that will define a point where this achieve the minimum. 
Now you would suspect that the solution would be simple, because this is a very simple quadratic form. and indeed the solution is simple, and if you look at it, you realize that if I want this to be 0, I want to this cancel out so:
$$\mathbf X^{T} \mathbf X \mathbf w = \mathbf X^{T}\mathbf y$$
you want this to happen, so you will get your zero. 
the interesting thing is that in spite the fact that the matrix $\mathbf X$ is a very tall matrix, definitely not square, hence no invertible, $\mathbf X^{T}\mathbf X$ is actually a square matrix, because the $\mathbf X^{T}$ is in x-axes way and the $\mathbf X$ is in vertical way, you multiply them and you will get a pretty small square matrix. 
And as we see, the chances are overwhelming that it will be invertible. 
So you can actually solve the equation above by inverting the  $\mathbf X^{T} \mathbf X$  you multiply by the inverse in the both side of equation and you will get:
$$\mathbf w = \mathbf X^{\dagger} \mathbf y$$
$$\mathbf X^{\dagger} = (\mathbf X^{T}\mathbf X)^{-1}\mathbf X^{T}$$
$$\mathbf X^{\dagger} is\ the\ pseudo-inverse\ of\ \mathbf X$$
$\mathbf X$ is non-invertible matrix, does not have an inverse. But it does have a pseudo inverse. and the pseudo-inverse have the interesting properties. for example $\mathbf X\mathbf X^{\dagger} = identity$ so it is okay to call it inverse in sort of.
this doesn't work the other way around, the other way around will give us a matrix interesting matrix which we will talk about later. 
If we were in a trivial situation where the $\mathbf X$ was a square, I have 3 parameters and I have 3 examples to determine them, this can be solve perfectly, I can get the $\mathbf X \mathbf w - \mathbf y$ to be zero, and how you get it to be zero? you would just multiply the proper inverse of the $\mathbf X$ in this case, and you will get $\mathbf X^{-1}\mathbf y$ so the $\mathbf X^{\dagger}\mathbf y$ is pretty much similar when you have a tall $\mathbf X$ and we are not going to get the zero, we are just going to get the minimum using pseudo-inverse.
### Pseudo-Inverse
$$\mathbf X^{\dagger} = (\mathbf X^{T}\mathbf X)^{-1}\mathbf X^{T}$$
this is the formula of pseudo-inverse that you need to compute in order to get the solution for linear regression. 
<!--![[Pseudo-inverse-01.png]]-->
![](https://i.imgur.com/bXCpyfg.png)

something is inverted, and when you see inversion in matrix you say, oh, computation, computation if this was a million by million I'm in trouble. so for this reason we want to know what kind of matrix we have here.
Well, nothing mysterious is about what's inside this.
<!--![[Pseudo-inverse-02.png]]-->
![](https://i.imgur.com/RAWwbjj.png)

you have this which is $\mathbf X^{-1}$, d is the length of your input, 1 is a added constant variable, so $d+1$ is a number of parameters, and the $N$, this is the scary one, this is the number of example, that could be in thousands. now you multiply this by $\mathbf X$
<!--![[Pseudo-inverse-03.png]]-->
![](https://i.imgur.com/3GAimcC.png)

but the good news is that when you go to $-1$ in the top right of the matrix multiply, I will have to be deal with a simpler guy. 
<!--![[Pseudo-inverse-04.png]]-->
![](https://i.imgur.com/xNDJMuk.png)

this is what you computationally doing. And if you look at what's inside here, it completely shrinks. 
<!--![[Pseudo-inverse-05.png]]-->
![](https://i.imgur.com/hpcvcTX.png)

That is what the matrix inside is. and you can see in this case we only had 3 parameters so this would be 3x3 matrix but imagine it with raw parameters it would be 257x257 matrix not that hard but still. 
And keep this in mind that there is so many packages for computing the pseudo-inverse, or outright getting the solution for linear regression, that you will never have to that yourself, if you want to something specialized. 
<!--![[Pseudo-inverse-06.png]]-->
![](https://i.imgur.com/wKfsHuI.png)

and this will get multiply by the $N$x1 $\mathbf y$ matrix which will result in the d+1x1 matrix that you will get all your w's 
## Linear Regression Algorithm
<!--![[Linear-regression-algorithm.png]]-->
![](https://i.imgur.com/ipKfnk8.png)

now you can call this one step learning if you want, with PLA it was more look like learning, because you had initial hypothesis then I take one example at a time, and figure out what is going on, and after a 1000 iteration I will get something. It looks like more like what we learn, we learn in steps.
This look like cheating, you gave me the thing and then you have the answer. Well as far as we are concerned, we don't care how you got it. if it's correct and it gives you a correct $E_{out}$ , you have learned.
And because this is so simple, this is a very popular algorithm that is used often, and used often as a building block for other guys. We can afford to use it as a building block, because the steps here will be so simple, that we can become more sophisticated in using it.
## Linear Regression for Classification
You can use linear regression not only for a real-value function, for regression problems. But you are also going to be able to use it for classification.
* Idea: linear regression learns a real-value function $y = f(x) \in \mathbb R$
* Observation: binary-valued function, which are the classification functions, are also real-valued! $\pm 1 \in \mathbb R$ --> so linear regression is not going to refuse to learn them as real numbers. 
* Use linear regression to get $\mathbf w$ where $\textcolor{red}{\mathbf w^{T}x_{n}} \approx \textcolor{blue}{y_{n}} = \pm 1$ --> so for every example, the actual value of the signal is close to the numerical +1 and numerical -1, that is what linear regression does.
* In this case, $sign(\mathbf w^{T}x_{n})$ is likely to agree with $y_{n} = \pm 1$
now having done that with the $y_{n} = \pm 1$ you realize that in this case, if you take the classification version of it, you take the sign of that signal in order to be able to classify as +1 or -1. If the value is genuinely close to +1 or -1 numerically, then the chances are when it's +1 the $\mathbf w^{T}x_{n}$ would be positive, and when it's -1, $\mathbf w^{T}x_{n}$ be negative.
The chances are you getting close to a number, you'll probably cross the zero doing that. and if you cross the zero, the classification will be correct. so if you take $\mathbf w^{T}x_{n}$ and then plug it as weights for classification, you will likely get something likely to agree with +1 and -1.]
* Good **Initial** weight for Classification
That is a pretty simple trick, because it's free. all you have to do is to have a classification problem. Let's run linear regression, It's almost for free, do this one-step learning, get a solution, and use it for classification. 
Well the weights are good for classification, so to speak, just by conjecture. But they also may serve as a good initial weights for classification. 
Remember that the perceptron algorithm, or the pocket algorithm, are really very slow to get there. You start with a random guy, Half the guys are misclassified, and you just going around trying to correct **one**, messes up the others, until it gets to the region of interest. And then it converge. Why not give it a jump start. Why not run linear regression first, get the w's. We know that the w's are OK, but they are not tailored to the classification But they are good initial condition. Feed those to pocket algorithm, and let it run to the solution. 
<!--![[linear-regression-for-classification.png]]-->
![](https://i.imgur.com/mili0Wp.png)

blue is the +1 class and the red is the -1 class, and we tried to find, what is the linear regression solution. Now remember that the blue region and the red region is belong to the classification. When you talk about linear regression, you have the value as a black bold line, and the signal there is 0. 
when you go higher the signal is positive, more positive and more positive. And when you go down the signal is more negative, more negative, more negative. There is a real valued function that we are trying to interpret as classification by taking the sign.
Now if you look at what the linear regression is trying to do when you use it for classification, all of the guys in the red region have a target value -1. It is actually trying to make the numerical value equal -1 to all of them. and when you go down further the number will get lower like -2, -3 and etc. and the linear regression is very sad about that.
It consider this as an error, in spite the fact that, when we plug it into classification, it just has the correct sign. And that's we all cared about. It is actually trying very hard to make all of under line region points -1 at the same time, which obviously cannot. And this is the problem with linear regression. 
In its attempts to make the -8, -1, it will move the boundary toward the to middle of the red region. And now it is very happy because it minimized the error function. But it's not really the classification. Nonetheless, it's a good starting point. And then you take the classification now, that forgets about the value and tries to adjust it according to the classification. And you will get a good boundary.
That's the contrast between applying linear regression for classification and linear classification outright. 
## Nonlinear Transformation
### Linear is Limited
You probably realize that, even when you dealing with non-separable data, we are dealing with non-separable data that are really basically separable with just few exception.
But in reality when you take a real problem, a real life problem, you will find that the data you are going to get could be anything. 
<!--![[Linear-limited-01.png]]-->
![](https://i.imgur.com/dK8SvZy.png)

in the classification paradigm I can put line anywhere, and I will still be in trouble, because this data is not linearly separable even by long shot. You can look here and say: I can see the pattern here. Closer to the center you have blues and closer to the peripherals you have red. So it could be very nice if I could apply the hypothesis that look like this:
<!--![[Linear-limited-02.png]]-->
![](https://i.imgur.com/N605f63.png)

the only problem is that, this is not linear, we don't have the tools to deal with that yet. Wouldn't it be nice if in two viewgraph, you can use linear regression and linear classification, the perceptron or the pocket, to apply it to this example.
### Another Example of nonlinearity
* Credit line is affected by 'years of residence'
We take the credit line, now if you look at the credit line, it is affected by the years of residence, we argued that if someone has been in the same residence for a long time, there is stability and trustworthiness. And someone has been short time, there is a question mark.
Now one thing is to say this is a variable that affect the output. Another thing to say is that this is the variable that affect the output linearly. 
* but not in a linear way
It would be strange if I'm trying to determine a credit line, to decide that the credit line will be proportional to the time you have lived in residence, because if you live 10 years, 20 years I will give you twice the credit line. It doesn't make sense. Because the stability is established probably by the time you get to 5 years. After that, it's diminishing return. 
So It would be very nice If I can instead of using linear one, define the non linear features which is * the following: $[[\mathbb[ x_{i} < 1]]$ and $[[x_{i} > 5]]$ are better.
let's take the logical condition, that the years of residence are less than 1, and in my mind I'm considering that this is not very stable. You haven't been there for very long. And another guy which were there for more than 5 years, so you are stable. The notation here, when I put something between these brackets, means this returns one of the condition is true and returns zero if the condition is false.
Now if I had those as variables in my linear regression, they would be much more friendly to the linear formula in the deciding the credit line(cause they are returning 0, and +1 and the linear regression trying to find the hypothesis that the values of the points be near -1 and +1), rather than the crude in put(just giving the line of residence).
But these are nonlinear function of $x_{i}$, and again we have the nonlinearity and we wonder if we can apply the same technique to the nonlinear cases or not. 
* Can we do that with linear model?
The key Question to ask is, **Linear in What?**
### Linear in What?
* Linear Regression implements
$$\sum_{i=0}^{d} w_{i}x_{i}$$
* Linear Classification implements
$$sign(\sum_{i=0}^{d} w_{i}x_{i})$$
This is a linear formula, and the algorithm being simple depends on the inside part being linear, and then you just make the decision based on that signal.
Now, these things you think are called linear because they are linear in the $x$'s which they are. I get these inputs, and I combine them linearly and I will get my surface, that's why I'm calling linear. 
However, you will realize more importantly, these guys these guys are linear in $w$.
When you go to the definition of a function to learning, the roles are reversed. 
The inputs, which are supposed to be the variable when you evaluate a function, are now constant, they are dictated by the training set. They're just a bunch of numbers that someone gave me.
The real variable as far as learning is concerned, are the parameters. The fact that it's linear in the parameters is what matters in deriving the perceptron learning algorithm, and the linear regression algorithm. If you go back to the derivation, it didn't matter what the $x$'s were. The $x$'s were sitting there as constants. And the linearity in $w$ is what enabled the derivation. 
Algorithms work because the **linearity in the Weights**.
Now this opens a fantastic possibility, because now I can take the inputs, which are just constants. Someone give me data And I can do incredible non-linear transformations to that data. And it will just remain more elaborate data, but constant. When I get to learn using the nonlinearity transformed data, I'm still in the realm of linear models, because the weights that will be given to the nonlinear features will have the linear dependency.
![[non-linear-transformation-01.png]]
![Uploading file...xhm0n]()

there is no limit, at least computationally, in terms of what you can transform $\Phi$, you can dream up really elaborate nonlinear transformations, transform the data and then do the classification.
There is a catch, and it is a big catch, we will discuss it in next Lecture.
## Q&A (Since min 59)