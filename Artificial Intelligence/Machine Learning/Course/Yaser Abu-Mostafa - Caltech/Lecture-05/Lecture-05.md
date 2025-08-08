## Lecture-04 Review
<!--![[Lecture-04-review.png]]-->
![](https://i.imgur.com/BYGDuRs.png)
Error + Noise --> relate the Learning Problem to Practical Situation
* Error measure, $e(h(x),f(x))$
Error measure --> to specify the error that is caused by your hypothesis $h$ --> estimate the cost of using your $h$, instead of $f$ (target function in full-information space/ideal target function/ which we need to use in the first place)
user can specify --> the price they want to pay when they are using $h$ instead of $f$ -->the principal way of defining error measure.
In the absence of that (which happens for quite a lot) --> resort to analytic properties, or practical properties of optimization --> to choose error measure
Once you define the error between the performance of your hypothesis versus target function on the particular point --> plug it to different error quantities --> the in-sample error and out-of-sample error + get those values in terms of error measure by getting an average. --> in In-sample Error $E_{in}(h) = \frac{1}{N}\sum_{n=1}^{N} e(h(\mathbf x_{n}), f(\mathbf x_{n}))$ you getting average by $\times \frac{1}{N}$ + in Out-of-sample $E_{out}(h) = \mathbb E_{x}[e(h(\mathbf x), f(\mathbf x))]$ the $\mathbb E$ (Expected value) handling the average 
* out-of-sample
And in the out-of-sample theoretically the definition would be that you also evaluate the errors between $h$ and $f$ on a particular point $\mathbf x$, give the weight of $\mathbf x$ according to its probability, and get the expected value with respect to $\mathbf x$.
* noisy target
The notion of noisy target came from the fact that what we are trying to learn may not be deterministic function, the only function in mathematics, where the $y$ is uniquely determined by the value of $\mathbf x$. But rather when $y$ is affected by $\mathbf x$, so $y$ is distributed according to a probability distribution, which gives you $y = f(\mathbf x) \rightarrow y \sim P(y \vert \mathbf x)$
when we had $\mathbf x$ being the only probabilistic thing and $y$ being deterministic function of $\mathbf x$ then your $\mathbf x$'s are independent from each other training samples are independent from each other then you compute each $y_n$ for base on function correspond to your $\mathbf x_n$,.
But in the noisy version, when you have distribution now the pair of your sample will still be independent, and the way that you generate them is $P(\mathbf x, y) = P(\mathbf x)P(y\vert \mathbf x)$
* Function Version --> independency --> the way that function work with different $\mathbf x$
* Noisy Version --> independency --> the pairs of $\mathbf x, y$ not only $\mathbf x$
and that's it for noisy target.
* Expected Value for Errors:
With noisy target, you now have to take into consideration the probability with respect to both $\mathbf x$ and $y$, so what it is used to be $E_{out}(h) = \mathbb E_{\mathbf x}[e(h(\mathbf x), f(\mathbf x))]$ respected to $\mathbf x$, is now $E_{out}(h) = \mathbb E_{\mathbf x, y} [e(h(\mathbf x), y)]$ expected value respected to $\mathbf x$ and $y$, and then you plug $\mathbf x$ to $h$ and then correspond it to the probabilistic value of $y$ that happen to occur. 
## Training versus Testing
![[Conceptual-distinction-example]]
the idea is to relate, in-sample and out-of-sample, in a realistic way.
Testing:
$$\mathbf P [\vert E_{in} - E_{out} > \epsilon \vert] \le 2e^{-2\epsilon^{2}N}$$
* $E_{in}$: how well you did on the final exam
* $E_{out}$: how well you understand the material
Training:
* $E_{in}$: What was your performance on the practice problems
* $E_{out}$: same as testing
$$\mathbf P [\vert E_{in} - E_{out} > \epsilon \vert] \le 2\textcolor{red}{M}e^{-2\epsilon^{2}N}$$
We want to replace $\textcolor{red}{M}$ which is the number of the hypothesis, with something more friendly.
because if you measure the complexity of your hypothesis set with only the number of your hypothesis this is next to useless for almost all cases, cause even in case of perceptron this $\textcolor{red}{M}$ is equal to infinity, which lead this guarantee notion to guarantee nothing.
We want a quantity that is not infinite even if your hypothesis set is infinite
### Where did this $\textcolor{red}{M}$ come from?
the bad events are $\mathcal B_{m}$:
$$\vert E_{in}(h_{m}) - E_{out}(h_{m})\vert > \epsilon$$
and there is a Union Bound for all bad events:
$$\mathbb P [\mathcal B_{1}\ or \mathcal B_{2}\ \dots \mathcal B_{M}]$$
we want the probability of any  $\mathcal B$s happen to be small --> cause now your algorithm is free to  pick any of these hypothesis and it will be fine, which is a good guarantee.
![[Ven-diagram]]
$$\mathbb P [\mathcal B_{1}\ or \mathcal B_{2}\ \dots \mathcal B_{M}] \xrightarrow[Disjoint]{\text{Union Bound}} \le \mathbb P [\mathcal B_{1}] +\mathbb P [\mathcal B_{2}] \dots \mathbb P [\mathcal B_{M}]$$
* In Principal/Theoretically: you can formulize this bad event in term of each hypothesis ($h_M$) and find the full joint distribution of all of your Hypothesis ($\mathcal H$) --> Complete Nightmare/Undoable
Abstract from hypothesis set a quantity that is sufficient to characterize overlaps + get us a good bound  - without having to go through intricate details of analyzing how the bad events are correlated

## Can we improve $\textcolor{red}{M}$ ? Yes! bad events are extremely Overlapping
![[Bad-event-in-perceptron]] 
## Notion that will replace the $\textcolor{red}{M}$
Quantity that Characterize the Complexity any Model you use
![[Attention-to-sample]]
these Perceptron's are different --> because they are different on at least one point in the input space 
* Because the input space is infinite --> we get infinite number of hypothesis --> (to solve this) restrict our attention only to finite set/sample
Powerful hypothesis: where I give you all the combination of red and blue
Weak Hypothesis: hypothesis where you get only a few combination
### Dichotomies: mini-hypotheses
The idea is that I give you $N$ points, and there is a dichotomy between what goes into red, and what goes into blue
* Dichotomy in Dictionary: a difference/division between two completely opposite ideas or things
![[Dichotomies]]
A hypothesis $h: D = \mathcal X \rightarrow R = \{-1, +1\}$ --> number of Hypotheses $\vert \mathcal H \vert$ can be infinite $\infty$
A dichotomy $h: D= \{\mathbf x_{1}, \mathbf x_{2},\dots, \mathbf x_{N}\} \rightarrow R = \{-1,+1\}$ -->number of dichotomies $\vert \mathcal H(\mathbf x_{1}, \mathbf x_{2},\dots, \mathbf x_{N}) \vert$ is at most $2^{N}$
### The Growth Function
The growth function counts the Most dichotomies on any $N$ points
$$\textcolor{red}{m}_{\mathcal H}(N) = \max_{\mathbf x_{1}, \dots, \mathbf x_{N} \in \mathcal X} \vert \mathcal H(\mathbf x_{1},\dots, \mathbf x_{N})\vert $$
The growth function satisfies:
$$\textcolor{red}{m}_{\mathcal H}(N) \le 2^{N}$$
![[Growth-function]]
> [!tip] Improvement
$\textcolor{red}{M}$ for set of all Hypotheses = $\infty$
$\textcolor{red}{m}_{\mathcal H}(N)$ for set of all Hypotheses = $2^{N}$
### Illustration
![[Positive-ray]]
![[Positive-intervals]]
![[Convex-set]]
> [!question] What is Convex region?
> A convex region is a region where, if you pick any 2 points within the region, the entirety of the line segment connecting them lies within the region

> [!tip] Growth Function Weakness
> Maximum, cause we are not going to get general point + we will have interior points (which eliminate many possibilities)

> [!question] why the Growth Function Weakness doesn't matter?
> Cause we don't want to keep studying the particular probability distribution, in a particular data set and more of this particulars, all we need is a Simple Quantity =  Maximum Overall = Simple Combinatorial Property
* The price we pay; the chances are the bound we are going to get is not going to be as tight as possible --> which is a normal price/normal tradeoff --> if you want a general result that applies to all situations, it's not going to be all that tight in any given situation
## What happens if $\textcolor{red}{m}_{\mathcal H}(N)$ replaces $\textcolor{red}{M}$?
$e^{-2\epsilon^{2}N}$ will kill the heck out of any polynomial you put instead of $\textcolor{red}{M}$ --> (which result in) probability to be diminishingly small --> which means you can Generalize --> if you could declare **"$\textcolor{red}{m}_{\mathcal H}(N)$ polynomial"** then learning is feasible
* Once you declare that a hypothesis set has a polynomial growth function, we can declare that learning is feasible using that hypothesis, period. -->if you're given enough examples, you will be able to generalize from a finite set, albeit big, to the general space with a probability assurance
## Proof that $\textcolor{red}{m}_{\mathcal H}(N)$ is polynomial
### Break Point
**if no data set of size $k$ can be shattered by $\mathcal H$, then the $k$ is a "Break Point" for $\mathcal H$**
$$\textcolor{red}{m}_{\mathcal H}(k) < 2^{k}$$
--> It's the point at which you fail to get all possible dichotomies.
Break point have a correspondence to the complexity of the hypothesis set --> higher Break point = more complex/stronger the hypothesis set
* For 2D Perceptrons, $k=4$ 
> [!tip] I don't need anything about the hypothesis set, just tell me the breakpoint and I will know the learning behavior
* A bigger data set cannot be shattered either --> if your brake point is 4 then you cannot get all the possibilities for 5 point
#### Examples:
* Positive rays: $\textcolor{red}{m}_{\mathcal H}(N) = N + 1 \rightarrow break\ point\ k=2 \ \textcolor{red}{\textbullet} \ \textcolor{blue}{\textbullet}$ 
* Positive intervals: $\textcolor{red}{m}_{\mathcal H}(N) = \frac{1}{2}N^2 + \frac{1}{2}N +1 \rightarrow break\ point\ k=2 \ \textcolor{red}{\textbullet} \ \textcolor{blue}{\textbullet}\ \textcolor{red}{\textbullet}$
* Convex sets: $\textcolor{red}{m}_{\mathcal H}(N) = 2^{N} \rightarrow break\ point = \infty$ 
### Result
$$\begin{cases}  No\ break\ point \implies \textcolor{red}{m}_{\mathcal H}(N) = 2^{N} \\
Any\ break\ point \implies \textcolor{red}{m}_{\mathcal H}(N)\ is\ \textbf{Polynomial}\ in\ N \end{cases}$$
> [!tip] when we can learn?
> In principle, if I just want to say you can use this hypothesis set, and you can learn, I just want you to tell me **I have a break point** 

* when we try to find the budget of example you need in order to get a particular performance then we will ask you the break point

### Puzzle
We have a break-point =2 and 3 data, find all dichotomies
<!--![[Puzzle.png]]-->
![](https://i.imgur.com/cF0gxAZ.png)

if you look at the schedule, this does not appeal to any particulars of the hypothesis set or the input space, other than the fact that the break-point=2.
I could be in a situation, where the hypothesis set cannot generate some of inputs for other reason, we are abstracting cause I don't want to bother to know the Input space and Hypotheses set, Just tell me the Break-point and I will try to find under that single constraint, how many can I possibly have? by the combinatorial constraint, we will have a restriction which is strong enough to get me a good-enough result.
