# Abstraction-and-reasoning-challenge

The code in the repository are our attempts to solve the Abstraction and reasoning Challent posed by Francois Chollet in 
this kaggle competition : https://www.kaggle.com/c/abstraction-and-reasoning-challenge

The competition asks if it is possible to build a model that can solve abstract tasks which are easy for a human but not 
straightforward within the current data intensive machine learning framework. We are given a handful of training examples (< 5)
each of which consists of an input image and an output image. The model is then required to generate an output image given 
an input (which is different from any of the training input images). It should be noted that the size of the input output pairs 
varies as we move along the dataset. The metric to evaluate scores an answer 0 if it is a perfect match to the output and 1 
otherwise. 

We are given 400 training tasks. Our initial naive idea was to use an LSTM which does not have any inbuilt priors and
given a test task which consists of the training examples - input/output pairs and a test input, we must generate an output.
However, despite numerous augmentations, the model almost never works. 

We also tried other naive approaches - CNN and decision trees. 

Our current approach fits within the framework of Neural program synthesis and is inspired by this article : 
https://www.microsoft.com/en-us/research/publication/robustfill-neural-program-learning-noisy-io/ by Jacob Devlin et al. 
Our DSL treats each connected component of a colour much like Robustfill treats words. We then have a few functions that enable 
one to change the colour of such components, move them around, and measure distances between components. 
