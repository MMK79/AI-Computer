* Machine learning models operate on floats not integers
1. Sequential is a class that describe the type of the model
	* It is Sequential because our layers will be added sequentially
2. Layers
	* Dense: Fully connected Neurons layer
	* Flatten: To convert 28x28 dimension data into 1 dimensional array
	* Activation Function
		* RelU: Rectified Linear Unit $\rightarrow$ It is pretty fast $\xrightarrow{why?}$ Because if the number is negative it will return 0, if it is positive it will return itself (On hardware we only check one bit - number is negative or positive)
			* Introduced by google
			* The great sum problem $\xrightarrow{RelU\ solution}$ Switch to 64 bit for an instance (Double precision will allow extend the dynamic range of calculation $\xrightarrow{cause}$ You can process larger number + Regularization Techniques)
				* Regularization: Weight get adjusted base on the amplitude of the signal and keep them low (not getting to that large numbers)
		* Sigmoid: With sigmoid you have exponent inside your formula, so there should be a lookup function for this $\rightarrow$ Several operation on cpu and gpu
			* Sigmoid introduced first, cause they think it might cause a great sum
		* Softmax: similar to sigmoid + it will normalize the entire layer [[DL-5.canvas|Softmax Group]] $\rightarrow$ Enable you to look at your output as a probability distribution
3. Solver
	* Optimizer
		* Gradient Descent
		* Adam
	* Loss function

> [!tip] Keras and Tensorflow are compatible with each other
> You can use tensorflow  function in keras

* You can set seed so you get the same result every time $\rightarrow$ good for research
* As a machine learning specialist you will try different topologies and architectures $\xrightarrow{Problem}$ How you can compare them to each other $\xrightarrow{solution}$ Validation Dataset, data that your model never seen not in training and not in testing (less cross contamination)
	* 80% train, 20% test
	  60% train,  20% test, 20% validation
	  70% train,  20% test, 10% validation

> [!tip] Think of neurons as your information hub

> [!Danger] Neural Network is kind of a Black Box

[[5-Dense-NN-MNIST.ipynb]]
# PCA
Principal Component Analysis $\rightarrow$ Mathematical Technique $\rightarrow$ How different are particular degree of freedom for whole the data set $\xrightarrow{at\ the\ end}$ suggest how much data is useful and how much you can drop
* PCA original from Information Theory $\rightarrow$ PCA is one of the ways to figure out what is the most important channel of the information and what will happen to your models if you modify them
[[5-PCA-MNIST.ipynb]]