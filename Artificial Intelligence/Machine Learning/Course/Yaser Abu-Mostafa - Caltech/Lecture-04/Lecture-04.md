## Review of Lecture-03
<!--![[Lecture-03-review.png]]-->
![](https://i.imgur.com/k71MVOr.png)

Linear models share what we would refer to signal, which is this formula:
$$\sum_{i=0}^{d} w_{i}x_{i} = \mathbf w^{T}\mathbf x$$
It's the linear sum involving input variables and weight, that can be put in vector form. And all linear models, in one form or another, have that as their basic building block.
* Classification - $h(x) = sign(\mathbf w^{T}\mathbf x)$
You can have a Classification linear system, like perceptron, that uses that signal and take the sign of it, to make decision 

* Regression - $h(x) = \mathbf w^{T}\mathbf x$
Real-valued, that take the signal as it is and has that as output. 

* Linear Regression Algorithm:
which was particularly easy algorithm, All it does it takes the input and put them in a particular matrix form, and then by computing $\mathbf w = (\mathbf X^{T}\mathbf X)^{-1} \mathbf X^{T}\mathbf y$ in one shot it can get you the optimal value of the weight vector.
* Linear models are Underestimate
However for linear models, it is remarkable how often they succeed on their own, and they are sufficient to get you the learning performance that you want. --> Try to use them when you are facing the learning problem first, and see if they actually achieve what you want.
* Strengthen the Linear model --> Nonlinear Transformation
The idea behind it is that the signal is not only linear in $\mathbf x$ is what you think of as the reason we call these linear systems. But actually they are linear in $\mathbf w$, and the reason is because learning actually modifies $\mathbf w$ in the learning process until it get to the optimal one, while $x$, which you usually think as a variable is actually a bunch of constant, that are the data sets that handed to you.
So Linearity in $\mathbf w$ is the key point. 
So if you take $\mathbf x$ and transform it in any way you form another vector $\mathbf z$ in a very nonlinear way if you want, this will still preserve <u>This Linearity (The Linearity in w)</u> And that all that matters for you to apply machine learning that we got.
## Error and Noise
Practical Considerations, that we have to take, when we consider real-life problems. And we are going to modify the learning diagrams that we have, by incorporating the notion of error and the notion of noise.

## Nonlinear Transformation - Continue:
<!--![[Nonlinear-transformation-01.png]]-->
![](https://i.imgur.com/3wG2C22.png)

There is no way to separate the blue from the red using the line, and the idea was to let's do non-linear transformation 
<!--![[Nonlinear-transformation-02.png]]-->
![](https://i.imgur.com/gMeLEUu.png)
<!--
for better understanding check [[No-->nlinear-transformation]]
<!--![[Nonlinear-transformation-03.png]]-->
![](https://i.imgur.com/oksCBYB.png)
![](https://i.imgur.com/S7pe7vZ.png)

when you do this you can get the separating boundary here, and that separating boundary is applied by applying your simple linear, like linear regression/ perceptron, to the data in the $Z$ space.
But we are not working in $Z$ space, When I give you a test point, it will still be in your original space $X$, and you have manage to separate things in the $Z$ space, well the way you do it is, you going back to the input space. (using inverse between quotation transformation '$\Phi^{-1}$', because the transformation in principle may not have inverse).
There might be some points in the $Z$ space that may not be a mapping of any point in $X$, and some point in Z space which may be the mapping to more than one point. And therefore, in spite of the fact that $\Phi$ is a mapping function, $\Phi^{-1}$ as we call it is not. 
But when you apply this figuratively, what you are going to get is a separating surface in the $X$ space that is not linear. And that was by applying purely linear methods.
<!--![[Nonlinear-transformation-04.png]]-->
![](https://i.imgur.com/g3Hnoqz.png)

And therefore, you can classify a new point by applying g of x, which would be the hypothesis that's defined here, the linear one, which happens to have another formula as you can see in the image. 
* Nonlinear Transformation Cycle
<!--![[Nonlinear-transformation-cycle.png]]-->
![](https://i.imgur.com/yIYfVDY.png)

1. You take data set
2. Transform it
3. Classify it
4. Interpret it
Although what we are illustrating here is the case that you go from the 2-dimension to another 2-dimension, In principal you can go from 2-dimension to 100-dimension, with high nonlinear coordinate, and the same principal will apply. you would classify things with hyperplane then and in the end your surface will be very very complicated. This enables you to implement a lot of sophisticated surface.
### What transform to what? 
* Each input
$$\mathbf x = (x_{0}, x_{1},\dots, x_d) \overset{\Phi}{\longrightarrow} \mathbf z = (z_{0}, z_{1}, \dots, z_{\tilde d})$$
Which each of $z$ coordinates, is a nonlinear function, potentially nonlinear function, of all $x$'s, all of the vector x. There is no limit. 
if you thought of linear model before transformation, as an economy car(it will get the job done, and that's it), the $Z$ is an 18-wheeler. And we most be proud of that, because with such a simple method, we can build a such strong machine. But be careful, because you may not be able to drive it.
If you do the wrong transformation, you will end up crashing (So many different type of crashing), which in this case will be Generalization-wise Crashing. That is although you did everything right, and you did this transformation, and this is a powerful machine, you don't know how to drive the powerful machine! and you end up with very poor generalization. 
And we need to get the theory in order to get our driver's license. That will tell us What to do in order to be able to drive this machine.
Whenever we need to distinguish between $z$ and $x$, we will add $tilde \sim$ to the $z$ counterpart, so you will not confuse about them. 
* Whole data set
$$\mathbf x_{1}, \mathbf x_{2}, \dots, \mathbf x_{n} \overset{\Phi}{\longrightarrow} \mathbf z_{1}, \mathbf z_{2}, \dots , \mathbf z_{n}$$
remember this is the inputs of the data set, and each of these $\mathbf x$'s by itself, is a full vector of $x$'s, now what they are transforming to? the $\mathbf z$'s. So you will end up with the <u>same number of points.</u> and each of the is a vector, and each vector can be very long according to the transformation you choose in the previous part. 
* The labels
$$y_{1}, y_{2},\dots,y_{n} \overset{\Phi}{\longrightarrow} y_{1}, y_{2},\dots,y_{n}$$
the data set comes with an inputs and outputs, I did transformation on the inputs, now what will outputs transform to? These are <u>Untouched</u>
* Weights
$$No\ Wights\ in\ X \ \ \ \ \ \ \ \ \ \ \tilde {\mathbf w} = (w_{0}, w_{1},\dots \dots, w_{\tilde d})$$
When we use linear models we have a weight vector, So when we are in the $X$ space, what are the weights? There are <u>no weights in $X$ space</u>
we are using $tilde \sim$ as nonlinear, so you know that you are in nonlinear space, so everything here is $tilde$
* Hypothesis
$$g(x) = sign(\tilde{\mathbf w}^{T}\mathbf z)$$
it will exactly the same, but it now is in the $Z$ space, it is little bit annoying because you telling me it's a $g(x)$ and you tell me that this is $\tilde{\mathbf w}^{T}$ times $\mathbf z$, where is my $x$?
$$g(x) = sign(\tilde{\mathbf w}^{T}\Phi(\mathbf x))$$
what $\mathbf z$ is, is the transformation of $\mathbf x$, So when you want to evaluate this for any $x$, all you need to do is plug into this formula and you are ready to go. 
## Learning Diagram - Review
When we face a real learning problem, we realize that there are components, practical components in real life, that we have not fully taken in consideration. And what we are going to do is to take the learning diagram, in the first lecture. And then we are going to adjust it according to these practical components, Until we get the final general form of the supervised learning diagram. 
<!--![[Learning-diagram-input-distribution.png]]-->
![](https://i.imgur.com/LF5bAAa.png)
## Error Measure
Error measure try to answer the following question: "What does $h \approx f$ mean?"
You have two functions, and you say this is a good/bad approximation, this is a qualitative statement, or is it quantitative?
It is quantitative and because it's quantitative, we are going to define an error measure, That measure how well, or how badly, h approximate f. 
So the error measure will be defined as:
$$E(h,f)$$
So It will return a number for any two function you plug in. One of them will be the target function, one of them will be the hypothesis of interest, and you will ask yourself how well, or how badly in this case the $h$ approximate $f$ and you get an error. 
If the error is an 0, then the $h$ perfectly reflects $f$ , and if there is an error then you might look for another $h$ that has an smaller error.
So that formalize the question of search, of learning algorithm, into minimizing the error function.
We call this error measure. It is neither a measure in the measure theoretic sense, or function (this is actually a functional. but we are not worrying about that.) We just take these two objects and return a number. And we refer to it as a function. And we talk about error measure in the sense of the English word "measure", not the mathematical measure.
Error function, in principal, return a number for a pair of functions. But it is almost defined in term of difference on a particular point, and then you put these point together. This was the **Pointwise Definition**
$$Pointwise\ Definition: e(h(x),f(x))$$
the value of $h$ in a particular point $x$, and the value of $f$ in the same point. This make sense cause I am trying to compare the function, I want them to be at the same point, Therefore if I compare them for every point this way, then I will get something meaningful, and then, I will need to do something about the different $e$'s That will give me the $E$.
Although this is not strictly required by the definition (you could have a crazy error function that does not reduce to corresponding points.) but invariably this is what you are going to do.
* Example:
$$Squared\ error: e(h(x), f(x)) = (h(x) - f(x))^2$$
$$Binary\ error: e(h(x), f(x)) = [[h(x) \neq f(x)]]$$
this notation mean, it will return 1, if the statement in it is true, and it will return 0 if it is false
### From Point-wise to Overall
The way that it's done is that the overall error, will always be average of pointwise error. All we need to do is that what we mean from "Average" in order to get that. 
* In-sample error
Let's look at the in-sample error:
$$E_{in}(h) = \frac{1}{N}\sum_{n=1}^{N} e(h(\mathbf x_{n}), f(\mathbf x_{n})) $$
think of in-sample error as the in-sample version of $E$, because now we are going to use the pointwise error that goes with that, error function in defining in-sample error. if you take a single point from your training set, you would be having $n$ going from 1 to $N$, and this is what we are going to average with respect to.
So you compute this error measure, whatever it may be, SE, BE and etc. and then you get the average.
if you look at what this formula return, it will return exactly the frequency error in the sample.
* Out-of-sample error
Again out-of-sample error is the Out-of-sample version of $E$, now in this case the point, is the general point in space, so we are labeling it as $x$, this could be any point in space that is picked from $X$, ,which is the input space, and in order to get the average in this case what you do is, to get the expected value, in this case with respect to $x$:
$$E_{out}(h) = \mathbb E_{x}[e(h(\mathbf x), f(\mathbf x))]$$
if you take the binary error, and if you take the expected value, this would be identically the probability of error overall. And we are using the probability distribution over the input space $X$, in order to compute this quantity.
That's how we get from the definition that you invoke on a single point, to in-sample and out-of-sample version.
let's revise the learning algorithm diagram with this component.
## The Learning Diagram with Pointwise Error
Realize that we are defining the error measure on a point.
<!--![[Learning-diagram-pointwise-error-01.png]]-->
![](https://i.imgur.com/Nu0lmsK.png)
The addition is that in deciding whether $g$ is close to $f$, which is the goal of learning. we test it with point $x$. And the criterion for deciding whether the $g(x)$ approximately the same as $f(x)$ is our pointwise error measure.
Furthermore, this $x$ is created from the space using something very specific, and that is, it comes from the same probability distribution that generated those points. 
<!--![[Learning-diagram-pointwise-error-02.png]]-->
![](https://i.imgur.com/5dZ6L6W.png)

This was implicit when we talked about the bin. $\mu$ was the probability distribution in the bin, and the $\nu$ was the sample distribution in the sample that you picked. 
When you test the system that you trained using certain probability distribution, I ask you to test it with points drawn from the same distribution. That's the only requirement in order to invoke Hoeffding, or the counterparts of Hoefding for more elaborate types of function.
Now, if you do that, then you have the guarantee, and it does make sense that with the beginning assumption, that $P$ can be an unknown, any probability distribution. All you are asked to do in order to get the guarantees that we talked about is: use it to generate the examples and use it to test hypothesis. 

## How to Choose the error measure
In defining the error measure, I'd like to get this case, because there is a great intuition about what is going on. So if we can come up with a meaningful error measure here, that captures both the "false accept" and the "false reject", we will have a handle on what the error measures are all about. 
How do we penalize each type?
When you give an error, you penalize it such that the error is large, so you move away from that hypothesis, to get a better hypothesis that doesn't penalize it that much. Now we can put it in matrix form:
<!--![[Choose-error-measure.png]]-->
![](https://i.imgur.com/zlqHtU2.png)
If I can come up with four numbers here, which I already know the two of them, then I have the answer. --> The key massage that we are conveying with this Discussion is that there is no inherit merit to choosing one error function over another. --> it's not analytic question! It's application-domain question!
we shouldn't penalize the false positive that much, if that will help us with the false negative, if you look at the matrix in this situation, this one qualifies:
<!--![[Choose-error-measure-supermarket.png]]-->
![](https://i.imgur.com/ao11NNV.png)

The false reject, It's you but were rejected, and you penalize it dearly.
The false accept, It's not you but you were accepted and therefore, you give a little weight. 
<!--![[Choose-error-measure-CIA.png]]-->
![](https://i.imgur.com/zOUMbLn.png)
So in this case, it makes sense that we are going to put the weights in the exactly opposite way than the supper market and even more extreme cause the price for false accept is too high but the price for the false reject is so low.
### Take-Home Lesson
when you are dealing with the practical learning problem, The Error Measure should be <u>Specified by the User</u>
you are going to deliver a system to them. The system is not perfect. They want the target function and you give them a hypothesis instead. You should ask them how much it does cost you to use my imperfect system in place of perfect system. That is their decision to make. And if they articulate that as the quantitative error function, this is the error function you should work with.
However, this does not always happen. People might not have the formalization that will capture the error measure in reality. And sometimes they capture it, but it is very difficult to optimize, and there are other considerations too.
So we need Alternatives to this Approach. and the alternative are a Compromise. They are very common and popular compromise, and people indulge them. I don't mind Indulging them, because actually, there are some nice properties to them. But you need to always remember this is the "Second Choice".
* Plausible Measure
if we knew what the error measure that needs to be used by the user is, we would use that. 
You resort to **Plausible Measure**, measures that you can argue analytically have a merit. Usually, the analytic argument start with an assumption, that is usually a loaded assumption. And from there, the going is very smooth. But Nonetheless, that is the absence of a meritorious measure, we might as well resort to that. 
$$Plausible\ measures: squared\ error \equiv Gaussian\ noise$$
that the corresponding error measure in this case would be squared error. So that is the plausibility of it.
You can go and get the Cross-Entropy type of error corresponding to the binary error and whatnot. So these guys have an error measure that goes with them. 
* Friendly Measure
You are not justifying that this is the meritorious measure, you're just using it because it's easy to use
$$Friendly\ Measure: closed-form\ solution, convex\ optimizatin$$
linear regression comes to mind, if you didn't use a squared error in that case, you would not have gotten the very easy formula that we started the lecture with.
Also, even if you can't get a closed-form solution, you might be able to use Optimization that is favorable. For example the cross-entropy that we referred to ends up, in a case of linear a linear model, the logistics regression, being convex which means that optimization is efficient. In that case, you get a global minimum and all of that. 
So now you resort to either the conceptual appeal, the plausibility, or the practical appeal, which is friendly aspect, to choose the error measure. This is completely legitimate, because in many cases, you're not going to user specified error.
## Learning Diagram with Error Measure
<!--![[Learning-diagram-error-measure.png]]-->
![](https://i.imgur.com/lecR4Kk.png)
The error function in learning diagram has two roles.
1. Evaluate the qualitative statement of $g(x) \approx f(x)$
the output, the final hypothesis, approximate the target function. the error measure is the thing that gives a grade, and you will use the error measure to quantify this approximate thing. 
2. Feeding to Learning algorithm
You have to feed the error measure to the learning algorithm, because what does a learning algorithm do, when you have error? it minimize the in-sample error, and the in-sample error depends on your error measure. 
## Noisy Target
The noisy targets are actually very important. Because in reality, these are the only types that you're going to encounter in problems in life. Very seldom you get a very clean target function. 
* The Target function is not always a function
function is a mathematical notion, you have to return a unique value for every point in domain. That is what qualifies it as a function. 
<!--![[Noisy-target.png]]-->
![](https://i.imgur.com/u6YSrAh.png)
so the last statement means that one point mapping to two values, so your target function is not really a function. Now what we do about that?
### Target Distribution
* We will use Target Distribution, as in probability distribution. so Instead of $y = f(x)$, we use target distribution: 
$$P(y\ \vert \ \mathbf x)$$
so again it depends on $x$, but it dependence is probabilistic. Some $y$'s are more likely than others in different cases, but in the previous notation only one $y$ was possible. so now we have something more accommodating. 
$x$ used to be generated by the probability distribution, it will still be generated by that distribution. This is an artifact that we introduced to get the benefit of the Hoeffding-type inequalities. But what will change now is that, instead of $y$ being deterministic of $x$, once you generate $x$, $y$ is also probabilistic generated by $P(y\vert \mathbf x)$.
* So now you can think of $(\mathbf x, y)$ being a generated by a joint distribution (assuming independence): 
$$P(\mathbf x)P(y\vert \mathbf x)$$
so in this case, there is no assumption of independence once you put it this way, But the assumption here is that the $P(y)$ your given is actually conditional on $x$
* What is a noisy target?
A noisy target can be posed as a deterministic target, like the one we had before + noise, this applies to any numerical target function. so if $y$ is real number, or binary, or something numerical, you can always pose the question of a target distribution as if it was a deterministic target function proper, plus noise.
This is just a convenience, to show you that $P(y\vert \mathbf x)$ is not that far from what we have already, and why?
$$Noisy\ Target = deterministic\ target\ f(x) = \mathbb E(y \vert \mathbf x)\ plus\ noise\ y - f(x)$$
Because if you define now a target function to be expected value -- the conditional expected value of $y$ given $\mathbf x$, that's function. Although $P(y\vert \mathbf x)$ gives you different values, you take the expected value -- that's a number, and you call this value of the function $x$, $f(x)$. then whatever is left out, you call the noise. 
So you get the bulk of it, and then you call the rest the noise. and that is usually form that is given. 
So you think you are really trying to learn the target function still, but there is this annoying noise, and you are trying to make your algorithm pick $\mathbb E(y \vert \mathbf x)$, and there is nothing you can do about the remaining noise, which averages to 0.
Now, by the same token, there is no loss of generality when we talk about probability distribution. If you actually have a proper function, which happens once in a blue moon, you can still pose this as a probability distribution. How do you do that?
* Deterministic target is a special case of noisy target:
$$P(y\vert \mathbf x) is\ zero\ expect\ for\ y = f(x)$$
So if we talk about finite domains, you put all the probability 1 on $y = f(x)$ and the probability zero on the other values. 
If it happens to be continues, which is almost always the case, you put all the mass on the point, you put delta function there, and you let the other once identically 0. 
In this case, the target function is probability distribution. Therefore if we decide that the targets always a distribution, there is no loss of generality.
## The Final Learning Diagram
<!--![[Final-leanring-diagram.png]]-->
![](https://i.imgur.com/vZpbHxw.png)
Now the Unknown target function, become Unknown target distribution. You define it as a conditional probability distribution of $y$ given $x$. And you can think of this as if it was a target function, which is the expected value that we talked about, plus noise, which is the remaining part. But as a target, it is a distribution.
* Unknown Target Distribution: accommodate a practical consideration, which is the fact that we are learning something noisy
* Error measure: Specification of penalty, or cost you pay for not being perfect, needs to be specify by the user. 
* Probability Distribution: our Artificial addition to the problem in order to make learning feasible
## Distinction between $P(y\vert \mathbf x)$ and $P(\mathbf x)$
* $P(\mathbf x)$ artificially introduce to accommodate Hoeffding.
* $P(y\vert \mathbf x)$ to accommodate the fact that genuine function that you are encounter in practice are not function - are actually noisy distribution.
<!--![[Distinction-between-input-target-distribution.png]]-->
![](https://i.imgur.com/VPytUF5.png)
### Similarities:
* Both pour in training examples
They look very much related, They both pour into the training examples. That's how the training examples are generated, each one passes their own probability, and when they are joining hands in Training example, it takes both and according to joint distribution generate training data. so they are in the same category.
* Both unknown
Both of them are unknown, the target distribution is unknown so my machine learning statement can be as general as I can afford. You are learning something and you don't know what it is, so that's good to have. 
Input distribution is unknown because it is the most assumption we could afford in order to get Hoeffding, we needed a probability distribution but we didn't make any assumptions about it. So we left it to be arbitrary one, and unknown, and we don't want to know it. 
### Difference:
* You are trying to learn Target distribution $P(y\vert \mathbf x)$
You are not trying to learn the input distribution. As a matter of fact when you are done, you will now know what the input distribution is. The input distribution is merely playing the role of quantifying the relative importance of the point $\mathbf x$

### Example:
You are approving credit: 
The target distribution is the probability of creditworthiness given the input. let's simplify the input and say it is salary. 
So I give you the salary, you decide what is the risk of this person defaulting, and then decide - output is +1, approving credit with probability 0.9 and disapprove credit with probability 0.1, this is the target distribution and this is what we are trying to learn. You're going to approximate it to hard decision probably, or you can actually learn the probability distribution as we see later on. 
The input distribution just tells you the distribution of salaries in the general population. How many people make 100,000 thousand, how many people make 10,000 thousand and etc. So in spite of the fact that the probability distribution over the input matters, in the sense that: let's say that you encounter a population where the salaries is very high, so the $P(x)$ is tilted very much towards high salaries, and let's conjecture that the high salaries correspond to high creditworthiness. 
In this case the same system that you trained, that will take any salary, high or low, and then decide whether to approve the credit or not, will be tested mostly in the very comfortable region of high salaries. So it will returns: yes approved, yes approved with a small probability of error.
And if you go and put the mass of the probability around the borderline cases, the cases where the decision is difficult, the same system that you learned will probably perform worse, just because there are so many points that are borderline.
So it will gives the weight that will finally grade your hypothesis, but you're not trying to learn that distribution. 
### Merging
<!--![[Merging-distribution.png]]-->
![](https://i.imgur.com/7UNlrNR.png)

And when you put them together analytically, which you are allowed to do, you can merge them as $P(\mathbf x , y)$ it is very nice and pleasant, and you generate the examples using that joint distribution.
However, you just need to remember that this merging mixes two concepts that are inherently different. 
Definitely $P(\mathbf x, y)$ is not a target distribution for supervised learning. the target distribution is $P(y\vert \mathbf x)$ and the other components are just a catalyst in the process.
## Preamble of Theory
What we know so far:
* learning is feasible in a probabilistic sense. --> by stating that the out-of-sample performance is close to in-sample
is this really learning? well learning means that you got the hypothesis right. so the condition of learning is that $g \approx f$ and as you can see this condition is not $E_{out}(g) \approx E_{in}(g)$. 
so what does $g \approx f$ in terms of $E_{out}$ and $E_{in}$ means? very simple $E_{out}(g) \approx 0$
Because out-of-sample error measures what? measure how far you are from the target function over the entire space. 
$E_{out}(g) \approx 0$ is what we want, and $E_{out}(g) \approx E_{in}(g)$ is what we have, So what is this?
It was good generalization. + Important building block --> because you will never have access to $E_{out}(g)$, if you had $E_{out}(g) \approx 0$ as condition, then you say: the quantity that I will never know is close to 0. Thank you very Much!
But now with the Theory, we were able to tell you, that you have a window on $E_{out}$ by dealing with $E_{in}$ if you have the right checks in place, we developed vaguely as the number of the hypothesis is not too big. And we will define it very, very accurately when we get to the theory part.
So if you have that, all of a sudden, $E_{in}$ is an important quantity, because now it acts as proxy for $E_{out}$ that you don't know. --> so it is not a total waste, but half of the story. 
The full story of learning has two question
## The 2 Question of Learning
$E_{out}(g) \approx 0$ patently is: we learned well. and this is achieved by:
$$E_{out}(g) \approx E_{in}(g) AND\ E_{in}(g) \approx 0$$
you put these 2 together and you have the learning. the first part is a theoretical result ([[Lecture-02|Lecture-02]]), and the second part is practical result([[Machine Learning/Courses/Mahdie Soleimani/Lecture-03|Lecture-03]]). 
1. Can we make sure that $E_{out}(g)$ is close enough to $E_{in}(g)$?
2. Can we make the $E_{in}(g)$ small enough?
<!--![[What-theory-achieve.png]]-->
![](https://i.imgur.com/j7qjdSZ.png)

## Q&A (Since min 60)
