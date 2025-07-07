![[Programming-Hierarchy]]
# Tensorflow Purpose
Optimize Hardware usage
* Math Kernel Library Intel $\rightarrow$ Numpy (bridge between Python and C)
* Cuda $\rightarrow$ CudNN
## Tensorflow 1.0 vs Tensorflow 2.0
In 1.0 Computation Graph was the default behavior (fast)
In 2.0 we have Eager Execution as our default behavior (pretty good for debugging) and when we done with our debugging we get back to Computation Graph
* Pytorch already had eager execution from start