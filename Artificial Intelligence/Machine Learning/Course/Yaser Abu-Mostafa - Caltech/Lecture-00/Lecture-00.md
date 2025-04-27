[Lecture-00 Link](https://youtu.be/2no-JUe8I9k?si=8ril8abn2aNHR5CB)
[Playlist Link](https://youtube.com/playlist?list=PLvx5ei9aEEqKgDZ7oaQGSToFi-QER4v1M&si=pcF9L34CxLDyv06l)
<!--![[Machine-Learning-Vocab.png]]-->
![](https://i.imgur.com/3GofBCu.png)

<!--![[Lecture-map.png]]-->
![](https://i.imgur.com/hSh260B.png)

## Theory:
means <u>that you mathematically models what happens in reality</u> and <u>then try true to do mathematical derivation in order to arrive at results</u> <u>that are not otherwise obvious</u> this is theory in general.
And there are usually two aspects when you look at the theory <mark style="background: #FF5582A6;">what assumption they made?</mark> and then <mark style="background: #FF5582A6;">what is the derivation is in order to get to the results</mark>
I hardly ever saw a situation where there is a problem with the second part, people are very competent mathematicians they are not going to make mistake in derivation, so the chances are when they make a statement mathematically they actually mean it and they proved it, so that is not our concern.
the biggest pitfall in theory is that people make assumptions that make what they are solving really divorced form the practice that you are going to see when you use machine learning
so when I picked the theory I picked it with relevance to practice I wanted to get something it has too be seen in mathematics and has to been proved and all of that but when you see the result you can use it, and I will go through other alternatives that have succeeded in that to different degrees.
### VC Theory (Vapnik–Chervonenkis)
The main Theory in machine learning, it is relevant you do the math you go through the proof and then you get the VC dimension you will equate it to the number of parameters in some cases and when you got to practice even if you're taking bonds and treating them as if they were equalities that leap of faith works very very well in practice. 
so it's not like that theory was the and then we decided that this is the good one, the theory was there and then we try to take wisdom from theory and apply it in practice and it worked.
this is the value added by choosing a topic and putting it here, you know the reason why it's here and the reason is that it is actually relevant to the practice 

### Bias-Variance:
sort of sweet little theory and it gave us some intuition about this and indeed it was included it was sort of low cost to include and it does lead to some understanding like the learning curves and whatnot

### Computational Complexity:
basically treat machine learning as a branch of Computational Complexity with an emphasis on asymptotic results so the question is, you know; can I do this problem in time or not? and it's very respectable body of work the only question for including it or not is, whether these particular results correspond to something that I face in practice.
When I look at it should I do computational complexity part of it or should I do the generalization part of it the generalization part of it one hand down because it's the one that is the bottleneck when I practice machine learning

### Bayesian:
This treat machine learning as a branch of probability. so you have a problem we can always put probability distribution and by the time you put the full joint of probability distribution you can answer all questions.
it's a very sweet theory because you can sort of ask any question you want and you will find a very concreate rigorous mathematical answer to that question if you have the set of joint probability distribution 

**There are other theories but these are kind of biggest players**


## Techniques:
the bulk of machine learning we covered some techniques but I'm going to categorize techniques into two sets and give you samples and then you will understand from what we have done and where it lies and how you can pursue it further

When you look at techniques you should separate;

#### models:
as in hypothesis sets and algorithms that go with them one category
* linear: we emphasized a lot it is not usually emphasized in regular machine learning courses they usually go for other models it is emphasized in statistics, and I find it to be very underrepresented in machine learning, it's a very important model with the non-linear transform you can cover a lot of territory and it is very low cost and it should be tried in many learning problems 
* Neural Networks:
* SVM
* Nearest Neighbors: related to RBF, it is a good benchmark if you have a data set why don't you categorize everything to the nearest neighbor and this will give you a performance and then you can compare others to that, it is not that difficult to implement 
* RBF
* Gaussian Processes: it has the same spirit of Bayesian, it is full probability distribution, a process here means a random process and the random process is nothing but a random function and the variable is random number, a random process is random function okay? so we have probability distribution over different functions that can come out and the assumption here is that they are Gaussian, which means that if you take any finite number of points the probability distribution of the $y$ coordinate is jointly Gaussian for those guys. so if you have full description of that probability distribution you solve anything you want because you can see if I have this data point then I'm conditioning on that Gaussian variable being equal to that and then I'm asking myself what is not the conditional distribution of the other points and for the Gaussian this is completely solved and you have nice matrices to just multiply out and get that solution so it's very good to use and if you are modeling something that happens to be Gaussian Process then obviously you win greatly because you are actually matching them
* SVD (Singular Value  Decomposition): use figuratively in this case, this is the factor analysis we used in Netflix problem, when we represent users as a bunch of factors and the movie as a bunch of factors and we try to match, when you put this you find that as if you are decomposing the entire rating matrix into two matrices and this would be similar to singular value decomposition in mathematics so we have seen part of that
* Graphical Model: it is almost a different paradigm on its own right, they are the model for where the target is the joint probability distribution, that's what you are trying to learn, and the key here is that the joint probability distribution between a large number of variable becomes very difficult to manage computationally, because there is numbers of possibilities would exponentially will be in number of variables, so the bulk of graphical model is to find simple way or an efficient way in order to get answers about that joint probability distribution and to learn it, so it is mostly computational. it's based on graph algorithms and the main aspect of putting it in graph is to use properties that happen to be conditional independence as a way to simplify the graph - **it can have full course about graphical model** --> if you are in the business of modeling joint probability distribution and computation is consideration this is the thing to learn there is no question about it, it is specialized but it is very helpful 

#### methods:
high level methods like regularization for example that doesn't restricted itself to particular model but is super impose on anything you use

* Regularization
* Validation
* Aggregation (not covered in this course)
* Input Processing: this is something that you will use regardless of the model you are going to use, AND it is best taught within project courses, it is very practical matter, when you teach a project course and people will have to work with real data it's a good thing to start by telling them okay here is the principal component analysis in order to normalize and correlate the inputs and outputs and this is the value and then they can try. there is sort of little intellectual value to input processing it's a practical matter and therefore it is best when you are teaching a practical course
## Paradigms:
meaning different assumption about the learning situation, not mathematical assumption but different assumptions that deal with different learning situations like: supervised learning versus reinforcement learning and when you make this assumptions the problem that you are solving are sufficiently different that you end up with really a different body of knowledge that you have to study and therefore we call them different paradigms

### Supervised learning:
the most popular and most useful form of machine learning --> problem in 
supervised learning with the question of information --> do I have enough information in the data in order to get the target function and generalize 

### Unsupervised:
only one algorithm --> clustering is the key

### Reinforcement learning:
you don't have target value on the example you just take an action, which is an output not the necessarily the target output and then something comes it tells you that you did well or or you didn't do well, so it sort of reinforcement of good action and elimination of bad actions will make you eventually converge to a good solution
So it is completely different from supervised learning in here the question is question of algorithm that will take all of these tons of examples that you can generate at will and produce a way to converge to a solution from one strategy to better strategy and better strategy

### Active Learning:
it could be active reinforcement or active Supervised, in active learning means that instead of someone giving you the data set you query about the value at a particular point, so you give me input and ask for the output if it's supervised or you give me the input and expect the reward or punishment in reinforcement learning, so it's an adjustment and there are some interesting results there

### Online Learning:
this is purely computational consideration, instead of giving you the full data set and allow you to work with it any way you want I am streaming the data set to you, so you will take something and you will try to modify your current hypothesis and then you take another part of data, AND you cannot store everything if you could store everything then you had the whole data set, so there are limitation on storage and computation under those constraint you ask yourself how can I learn how close can I get to the optimal as if I had the whole data set and what

