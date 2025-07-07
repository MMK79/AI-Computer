Problem: find the best weight ($w$) and bias ($b$)
1. Start with a random $w_{guess}$ and $b_{guess}$
2. Do prediction base on the current line, how $\mathbf y_{predict} = w_{guess}*\mathbf x + b_{guess}$
3. Calculate Loss function (a way to measure our performance)
   In this case we will use Mean Squared Error (MSE)
   $$MSE = \frac{(\mathbf y_{predict} - \mathbf y_{real})^{2}}{n}$$
4. Now we need to Optimize Loss Function $\xrightarrow{how}$ Gradient Descent $\xrightarrow{problem}$ It can overshot from the optimal point $\xrightarrow{solution}$ Learning Rate $\xrightarrow{problem}$ You may not find the optimal point or it will take such a long time $\xrightarrow{solution}$ Put limit on Step
* We calculate derivative with respect to each one of our $w$'s and $b$ $\rightarrow$ Gradient
* Learning rate control converge rate: how fast or slow you will get to the answer
	* Small learning rate $\xrightarrow{result}$ To many steps needed
	* Large learning rate $\xrightarrow{result}$ Overshoot
* Steps control the amount of your calculation
> [!question] How to find the optimal learning rate?