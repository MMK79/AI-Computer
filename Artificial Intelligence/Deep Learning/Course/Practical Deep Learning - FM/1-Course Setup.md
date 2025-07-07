# Jupyter Notebook
`ipynb` interactive python notebook
* One part of it is a web server $\xrightarrow{means}$ You can run it on other machine and if the ports are open you can connect to it
* On Backend part of it: it is running several python interpreter $\xrightarrow{means}$ when you run your code it will run on the machine that is running your server, and if you print you will see the result on your web server in your machine

> [!warning] Conda Jupyter Server Problem
> `TypeError: __init__() got an unexpected keyword argument 'default'` error!
> Source of Problem: `referencing` and `jsonschema` versions are not compatible! (Conda should solve this itself!)
> Solution: `conda uninstall referencing` (result to its down grade not complete uninstall)
## Install Tensorflow
* `pip install tensorflow`
* `conda install tensorflow`
* run CLI command in Jupyter with `!` before your code
  `!pip install tensorflow`
# Resources
## Books
- "Deep Learning with Python" by [François Chollet](https://github.com/fchollet/deep-learning-with-python-notebooks)
- "Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow: Concepts, Tools, and Techniques to Build Intelligent Systems" by [Aurélien Géron](https://github.com/ageron/handson-ml2)
- "Hands-On Neural Networks with TensorFlow 2.0" by [Paolo Galeone](https://github.com/PacktPublishing/Hands-On-Neural-Networks-with-TensorFlow-2.0)
## Useful Links
* [Tensorflow Document](https://www.tensorflow.org/)