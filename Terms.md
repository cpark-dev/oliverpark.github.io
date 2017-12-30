# Support Vector Machine

##### Deep Learning
One of the most influential approaches to supervised learning is the support vector machine (Boser et al., 1992; Cortes and Vapnik, 1995). 

The support vector machine does not provide probabilities, but only outputs a class identity. 

##### Udacity
[Lesson 15: Support Vector Machines](https://classroom.udacity.com/nanodegrees/nd013/parts/fbf77062-5703-404e-b60c-95b78b2f3f9e/modules/2b62a1c3-e151-4a0e-b6b6-e424fa46ceab/lessons/29b49196-b5da-4eeb-8661-348fbe11a89a/concepts/9444768a-a172-4858-a711-13cd657f6ea6)

##### scikit learn
[1.4 Support Vector Machines](http://scikit-learn.org/stable/modules/svm.html)

Support vector machines (SVMs) are **a set of supervised learning methods** used for classification, regression and outliers detection.

When training an SVM with the Radial Basis Function (RBF) kernel, two parameters must be considered: C and gamma. The parameter **C**, common to all SVM kernels, trades off misclassification of training examples against simplicity of the decision surface. A low C makes the decision surface smooth, while a high C aims at classifying all training examples correctly. **gamma** defines how much influence a single training example has. The larger gamma is, the closer other examples must be to be affected.

Proper choice of C and gamma is critical to the SVM’s performance. One is advised to use sklearn.model_selection.GridSearchCV with C and gamma spaced exponentially far apart to choose good values.





# Decision Tree
##### Deep Learning
Another type of learning algorithm that also breaks the input space into regions and has separate parameters for each region is the **decision tree** (Breiman et al., 1984) and its many variants. 

##### Udacity
[Lesson 16. Decision Trees](https://classroom.udacity.com/nanodegrees/nd013/parts/fbf77062-5703-404e-b60c-95b78b2f3f9e/modules/2b62a1c3-e151-4a0e-b6b6-e424fa46ceab/lessons/3cd1d00f-ffb2-4030-bd33-ebc4b95c6740/concepts/114d5639-feb8-448d-95d1-869f40e77ed3)

##### scikit learn
[1.10. decision Trees](http://scikit-learn.org/stable/modules/tree.html)
Decision Trees (DTs) are **a non-parametric supervised learning method** used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features.

Use **min_samples_split** or **min_samples_leaf** to control the number of samples at a leaf node. A very small number will usually mean the tree will overfit, whereas a large number will prevent the tree from learning the data. Try min_samples_leaf=5 as an initial value. If the sample size varies greatly, a float number can be used as percentage in these two parameters. The main difference between the two is that min_samples_leaf guarantees a minimum number of samples in a leaf, while min_samples_split can create arbitrary small leaves, though min_samples_split is more common in the literature.



# Maximum Liklihood Estimation

*Likelihood: the state or fact of something's being likely; probability.*

##### Deep Learning

We would like to have some principle from which we can derive specific functions that are good estimatiors for different models. The most common such priciple is the maximum likelihood principle. 

We can thus see maximum likelihood as an attempt to make the model distribution match the empirical distribution $\hat{p}$~data~. Ideally, we would like to match the true data-generating distribution $p$~data~, but we have no direct access to this distribution. 

In software, we often phrase both as minimizing a cost function. Maximum likelihood thus becomes minimization of the negative log-likelihood(NLL), or equivalently, minimization of the cross-entropy. 

##### Udacity
Our goal is to maximize this probability. 

# Likelihood vs Probability

Suppose that you have a stochastic process that takes discrete values (e.g., outcomes of tossing a coin 10 times, number of customers who arrive at a store in 10 minutes etc). In such cases, we can calculate the probability of observing a particular set of outcomes by making suitable assumptions about the underlying stochastic process (e.g., probability of coin landing heads is $p$ and that coin tosses are independent).

Denote the observed outcomes by $O$ and the set of parameters that describe the stochastic process as $\theta$. Thus, when we speak of probability we want to calculate $P(O|\theta)$. In other words, given specific values for $\theta$, $P(O|\theta)$ is the probability that we would observe the outcomes represented by $O$.

However, when we model a real life stochastic process, we often do not know $θ$. We simply observe $O$ and the goal then is to arrive at an estimate for $θ$ that would be a plausible choice given the observed outcomes $O$. We know that given a value of $θ$ the probability of observing $O$ is $P(O|\theta)$. Thus, a 'natural' estimation process is to choose that value of $θ$ that would maximize the probability that we would actually observe $O$. In other words, we find the parameter values $\theta$ that maximize the following function:

$L(\theta|O)=P(O|\theta)$

$L(\theta|O)$ is called the likelihood function. Notice that by definition the likelihood function is conditioned on the observed $O$ and that it is a function of the unknown parameters $\theta$.

https://stats.stackexchange.com/questions/2641/what-is-the-difference-between-likelihood-and-probability


# Linear Regression & Mean Squared Error(MSE)

##### Deep Learning

Our definition of a machine learning algorithm as an algorithm that is capable of improving a computer program's performance at some task via experience is somewhat abstract. To make this more concrete, we present an example of a simple machine learning algorithm: **linear regression**. 

In other words, the goal is to build a system that can take a vector $x \in \mathbb{R}$ as its output. The output of linear regression is a linear function of the input. Let $\hat{y}$ be the value that our model predicts $y$ should take on. We define the output to be

​	$\hat{y} = w^\intercal x$

where $w \in \mathbb{R}^n$ is a vector of parameters. 

We thus have a definition of our task $T$: to predict $y$ from $x$ by outputting $\hat{y} = w^\intercal x$. Next we need a definition of our performance measure, $P$. 

One way of measuring the performance of the model is to compute the **mean squared error** of the model on the test set. If $\hat{y}$^(test)^ gives the predictions of the model on the test set, then the mean squared error is given by

​	MSE~test~ $= \frac{1}{m}\Sigma( \hat{y}$^(test)^$ - y$^(test)^)~i~^2^.

To make a machine learning algorithm, we need to design an algorithm that will imporve the weights $w$ in a way that reduces MSE~test~ when the algorithm is allowed to gain experience by observing a training set ($X$^(train)^, $y$^(train)^).

It is worth noting that the term linear regression is often used to refer to a slightly more sophisticated model with one additional parameter - an intercept term $b$. In this model 

​	$\hat{y} = w^\intercal x + b$

Instead of adding the bias parameter $b$, one can continue to use the model with only weights but augment $x$ with an extra entry that is always set to 1. 

We frequently use the term "linear" when referring to affine functions throughtout this book. 

**Notation**

$\mathbb{R}$	The set of real numbers

