* Statistics:
  Take a Batch, Observe it and Generalize it on The Whole $\rightarrow$ Extract meaning From data (Reduction)
	* Normal Distribution, Gaussian Distribution, Bell Curve Distribution (Cause it look likes a bell):
		* Mean
		* Standard Deviation (Width of Distribution) 
* Machine Learning:
  Evolution of Statistics, Take a bunch of Data and do the Feeding process on them $\rightarrow$ Distribution Analysis
	* Feeding Process:
	   Try to find the corresponding distribution and those 2 values which describe that distribution
* Deep Learning:
  Deep Learning Comes from this architecture of Neural Networks, where you have models with multiple layer of Neurons, which help us to jump from linearity to complex function, like AlexNet which won a competition from a SVM model by 20% difference in accuracy whit Convolutional Neural Network $\xrightarrow{Simply}$ Information Transformation in a higher level than ML
	* Neural Networks:
	  Imitate what Neurons do in brain
		* Neurons:
		  Get bunch of input signals and somehow decide what is important and what is not, and we have these neurons connected (chains together) to each other
	  ![[Single-Neuron]] Now we can have a layer of these Neurons, and even layers of neurons which connected to each other $\rightarrow$ Neural Network
	  ![[Neural-Network]]
	  What Model Learns is (Parameters): Weights ($w$) and Biases ($b$)
	  What We provide is (Hyper Parameter): Architecture of the Model (number of layers, neurons in each of them, how they connect)
	  How we train this Model? Training Dataset $\rightarrow$ Annotated Chunks of Data for each class
	  At start we initialize and activate Parameters randomly $\xrightarrow{now}$ Do Forward Propagation $\xrightarrow{now}$ You have a prediction, the trick is that you know the right answer so now you compare your prediction with the right answer $\xrightarrow{then}$ Back Propagation: reinforce good decisions and punish bad decisions by raising and lowering weights (calculate through derivative (more specific Gradient)) $\xrightarrow{now}$ Repeat the process
	  ![[Computer-Science-vs-Machine-Learning]]
	  After Model get trained, we Freeze the parameters and use it; by providing inputs that model never seen in training process
* AI:
  Turing Test $\rightarrow$ Computer be able to think/act like a human
  Deep learning Can't create anything $\xrightarrow{but}$ We can use it to create
  ![[AI]]
  > [!important] You can combine models and build your own model