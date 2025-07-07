* AlexNet:
	* Convolution layer/operation
		* Filter: it is like weights but in a different personality (matrix like)
			* Instead of having your input fully connected to your neural network now you connect it partially through your filter
				* Filter gives physical meaning to data, we look for features in our data
				  ![[Convolution]]
	* Pooling layer/operation: Choose a representation of a bunch (Compress Data)
		* Max Pooling: take a highest number
		  ![[Pooling]]
> [!tip] You want to have multiple Convolution layers!
> Cause the convolution layers are small, the first layer of your convolution probably learn the basic features, and for more advance understanding on data you need to have multiple layers of Convolution $\rightarrow$ Deeper you go, you see the bigger picture (combination of your little pictures)
* Each of your convolution units have bias too!
* Filter = Feature
> [!danger] When your accuracy for validation instead of improving or stabilizing goes down, means that you overfitted
> Stop right when your loss function is minimum

> [!tip] Bias Variance Tradeoff
> Bias: Incompetency of model to describe the training data
> Variance: Incompetency of model to describe the different batch of test data

> [!tips]
> To show the topology of the model
> ```python
> from tensorflow.keras.utils import plot_model
> plot_model(model, to_file='modle.png')
> ```
> For higher resolutions you can use SVG
> ```python
> from ipython.display import SVG
> from tensorflow.keras.utils import model_to_dot
> 
> SVG(model_to_dot(model).create(prog='dot', format='svg'))
> ```
> Save model
> ```python
> model.save('name')
> model.save_weights('name_weights')
> ```
> Load model: create the model with the same topology then load the weights
> ```python
> model.load_weights('name_weights')
> ```
> To use prediction feature you need to reshape and give a model list of data:
> ```python
> inp = x_test[0].reshape(1, 28, 28)
> res = model.predict(inp)
> ```

# Transfer Learning
> [!important] Keras downloaded model save in `~/.keras`
* Model use mini-batches in the training process, What does it mean?
   It means that in the training process, when they are calculating gradient, they are not calculating it for only one sample of data, instead they calculating gradient for a batch of samples then average that gradient and use it $\rightarrow$ Reduce Noisiness of changes for weights and biases, more stable training, Utilize Vectorization (Improve computation performance (use cmd instruction)) $\rightarrow$ Generalize model
* When you have so many classes it is recommended to use mini-batch