# Question 1:
For each of parts (a) through (d), indicate whether we would generally
expect the performance of a flexible statistical learning method to be
better or worse than an inflexible method. Justify your answer.
(a) The sample size n is extremely large, and the number of predictors
p is small.
(b) The number of predictors p is extremely large, and the number
of observations n is small.
(c) The relationship between the predictors and response is highly
non-linear.
(d) The variance of the error terms, i.e. σ2 = Var(e), is extremely
high.

# Answers:
## (a):
Flexible should be better. The small number of predictors means that
overfitting should be less of a problems. A large N means that fluctuations
would be less significant and less likely to 'distract' the model.
## (b):
Inflexible. Noise and fluctuations from small N would lead to overfitting 
with a flexible model.
## (c):
Flexible. An inflexible model would not be able to fit the data, and
would lead to a large bias in the model.
## (d):
Inflexible. A flexible model would fit the fluctuations too much and 
lead to an overfitted model with high variance.


# Question 2:
Explain whether each scenario is a classification or regression problem,
and indicate whether we are most interested in inference or prediction.
Finally, provide n and p.
(a) We collect a set of data on the top 500 firms in the US. For each
firm we record profit, number of employees, industry and the
CEO salary. We are interested in understanding which factors
affect CEO salary.
(b) We are considering launching a new product and wish to know
whether it will be a success or a failure. We collect data on 20
similar products that were previously launched. For each product
we have recorded whether it was a success or failure, price
charged for the product, marketing budget, competition price,
and ten other variables.
(c) We are interesting in predicting the % change in the US dollar in
relation to the weekly changes in the world stock markets. Hence
we collect weekly data for all of 2012. For each week we record
the % change in the dollar, the % change in the US market,
the % change in the British market, and the % change in the
German market.

# Answers:
## (a):
Regression. We're interested in making predictions and inferring which
predictors most strongly affect the response.
n = 500, p = 4
## (b):
Classification. 2 response classe - success and failure.
n = 20, p = 13
## (c):
Regression. "Interested in predicting..."
n = 52, p = 3
(% change in dollar is the 'y' in {xi, yi})

# Question 3:
We now revisit the bias-variance decomposition.
(a) Provide a sketch of typical (squared) bias, variance, training error,
test error, and Bayes (or irreducible) error curves, on a single
plot, as we go from less flexible statistical learning methods
towards more flexible approaches. The x-axis should represent
the amount of flexibility in the method, and the y-axis should
represent the values for each curve. There should be five curves.
Make sure to label each one.
(b) Explain why each of the five curves has the shape displayed in
part (a).

# Answers:
The squared bias decreases monotonically as flexibility increases, because
more flexibility means the model can fit the data more accurately.

Variance increases monotonically as flexibility increases. Variance is
a measure of how much f^ would change if the model was re-fit using a
new set of training data. A highly flexible model would be more likely to
overfit the data, and could be very different from a previous fit.

Training error decreases monotonically as flexibility increase. A more 
flexible model can more accurately fit the data. A highly flexible model has
training error = 0.

Test error has a U-shape curve. Initially it decreases as increased flexibility
gives an improved fit to the training data. Further increasing flexibility 
leads to overfitting, and the model will badly fit the test data because it
has just fit the noise in the training data.

Irreducible error is a flat horizontal line. A property of the underlying 
data/experiment.


# Question 5:
What are the advantages and disadvantages of a very flexible (versus
a less flexible) approach for regression or classification? Under what
circumstances might a more flexible approach be preferred to a less
flexible approach? When might a less flexible approach be preferred?

# Answer:
Advantages of a flexible model:
Less bias. More likely to be able to model a complex real-life problem.
Easier to interpret and infer how predictors affect response.
Disadvantages:
Higher variance. Higher likelihood of overfitting. More difficult to 
interpret model parameters.
See question 2 for applications where less/more flexible is preferred.


# Question 6:
Describe the differences between a parametric and a non-parametric
statistical learning approach. What are the advantages of a parametric
approach to regression or classification (as opposed to a nonparametric
approach)? What are its disadvantages?

# Answer:
In a parametric approach, the problem is reduced to estimating the 
parameters which define a particular function.
In a linear model for example: f(X) = b0 + b1 * x1 + b2 * x2 ...
only the parameters must be found.

In a non-parametric approach the form of the function must also be found,
or something like a spline can be used to fit the data.

The parametric approach is preferred when interpretabilty of the model is
important.


# Question 7:
The table below provides a training data set containing six observations,
three predictors, and one qualitative response variable.
Suppose we wish to use this data set to make a prediction for Y when
X1 = X2 = X3 = 0 using K-nearest neighbors.
(a) Compute the Euclidean distance between each observation and
the test point, X1 = X2 = X3 = 0
(b) What is our prediction with K = 1? Why?
(c) What is our prediction with K = 3? Why?
(d) If the Bayes decision boundary in this problem is highly nonlinear,
then would we expect the best value for K to be large or
small? Why?

# Answers:
## (a):

| Obs. | X1 | X2 | X3 | Y     | Distance        |
| ---- | --- | --- | --- | ----- | --------------- |
| 1    |  0 |  3 |  0 | Red   | 3.0             |
| 2    |  2 |  0 |  0 | Red   | 2.0             |
| 3    |  0 |  1 |  3 | Red   | sqrt(10) = 3.16 |
| 4    |  0 |  1 |  2 | Green | sqrt(5) = 2.23  |
| 5    | -1 |  0 |  1 | Green | sqrt(2) = 1.41  |
| 6    |  1 |  1 |  1 | Red   | sqrt(3) = 1.73  |

## (b):
Green. The point at -1, 0, 1 is the single nearest neighbour and is 
classified as green.
## (c):
Red. Three nearest neighbours are: p5, p6, p2 with classes Green, Red, Red.
The majority class is red. Therefore the prediction is red.
### Note:
The correct way of working this out is to use equation 2.12.
I.e. 

P(Y=red|x=x0) = 1/3 * sum I(yi = red) = 1/3 * (1 + 0 + 1) = 2/3

P(Y=green|x=x0) = 1/3 * sum I(yi = green) = 1/3 * (0 + 1 + 0) = 1/3

Therefore prediction is red.
## (d):
Best K value would be small.
A highly non-linear Bayes boundary would not be reproduced using a large K.
Including points which are not local to the test point would result in a 
smooth, more linear predicted boundary.
