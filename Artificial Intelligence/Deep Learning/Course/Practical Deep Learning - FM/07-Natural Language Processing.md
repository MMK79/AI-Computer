How to convert text to number?
Create a Vocabulary with one-hot-encoding vectorization $\xrightarrow{problem}$ You create a big arrays for each word (most of the values of that array is 0 too - sparse vectors)
# Embedding - Dimensional Reduction in Words
Instead of One-hot-encoding you provide a space for your words and let them find their own position in that space
* The problem with embedding is that position in it doesn't matter + uppercase and lowercase matters $\xrightarrow{solution}$ Recurrent Neural Network (try to remember the position of the word)
> [!tip] If you want to train your text analysis model, use pre-trained embedding

> [!important] Machine Learning and Deep Learning need you to build an intuition to find out what works and what not works
* When you work with Text Embedding process, the way you present word into machine is the most important part of the job