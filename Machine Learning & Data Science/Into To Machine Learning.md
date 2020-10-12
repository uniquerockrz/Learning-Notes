# Intro To Machine Learning

Machine Learning can be described as a study of training computers to do tasks without explicitly programming them.

## Types Of Machine Learning Systems
Machine Learning systems can be of many types, depending on number of factors.

* Supervised or Unsupervised: Supervised is where you feed the system training data and the model 'learns' from the data itself. Unsupervised is where the model itself finds patterns in the data without the external supervision of labels. Example: supervised - classification, unsupervised: clustering.
	* Semi supervised : an combination of above, where the model finds patterns in the data and then you label them. Example: photo name labels in google photos.
	* Reinforcement learning: The model learns the data based on a certain objective, like getting a reward or avoiding a penalty.  Example: Alpha Go game model by Google.
* Batch or Online learning: Batch learning is where the system must learn by taking all the data at once. Online learning is where the model can take incremental instances of data and learn from that.
* Instance based learning and model based learning: In instance based, the model takes the new data it has to predict, compares it to the data it already knows and gives the closest match result. Example: a decision tree. In model based learning, it generalizes to build an form, and then predicts the output based on the form. Example: linear regression. 

## Simple Example 
Let's take an example of one of the most rudimentary application of machine learning - predicting house prices. We use a very simple decision tree model here.

One of the easiest thing we can do is to divide houses by two categories according to rooms. And then take the average of each category to determine an approx house price. In python, this can be formed as:

```python
if rooms == 1:
	price = 100000
else:
	price = 150000
```

A decision tree looks up at the past data of house prices and build a model like above. This process is called fitting, and the data it builds the model on is called the training set.

We can go further with this decision tree by including more features (also known as predictors) which can be lot size, number of bathrooms etc. 

### Loading Up The Data And Doing Some Basic Explorations
We will use pandas, a python library to load up the data and do some basic explorations on that. 

```python
from pandas import pd

df = pandas.reas_csv('/home/srvmdk/HousingData.csv')
```

This loads up the CSV data and stores it into a dataframe which you can imagine as a table  or a matrix. You can get some summary statistics by using:

```python
df.describe()
```

This will give you stuff like mean, median, mode, count, min, max and the standard deviation of numerical features. 

If there are null or missing values, you can drop them using

```python
df.dropna(axis=0)
```

The axis determines whether you want to go by rows `0` or columns `1`.

### Selecting Columns For Model Training

You can choose a column by its name in dot notation. In this case, we will choose the target value we will build our model on. 

```python
y = df.SalePrice
```

You can use the columns attribute to see all the columns the dataset has.

```python
df.columns
```

There are several ways you can access multiple columns.

```python
X = df[['LotArea', 'YearBuilt', '1stFlrSF', '2ndFlrSF']]
X = df.iloc[[0:5,0:4]] # get rows 0 to 5, columns 0 to 4
```

### Build The Model And Predict Values

We use sklearn for this. 

```python
from sklearn.tree import DecisionTreeRegressor
melbourne_model = DecisionTreeRegressor(random_state=1)
melbourne_model.fit(X, y)
```

We specify a random state so that the results are same in each run. 

```python
melbourne_model.predict(X)
```

We then predict using the predict function.

### Validating The Model

The model takes up the shape of the training data. Hence, if we actually train and test the model on the training data, we won't be able to get the actual accuracy of the model. To overcome that, we split the data into a training set and a validation set, and then build the model on the training set and test it on the validation set.

```python
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_absolute_error

train_X, val_X, train_y, val_y = train_test_split(X, y, random_state = 0)
melbourne_model = DecisionTreeRegressor()
melbourne_model.fit(train_X, train_y)
val_predictions = melbourne_model.predict(val_X)

print(mean_absolute_error(val_y, val_predictions))
```

Here we are taking the mean absolute error to judge the model accuracy.

### Types Of Errors For Assessing The Model

The one we have used above is called mean absolute error. It is really simple, and just takes the absolute difference between the predicted and the actual value, and takes an mean of it. 

Another most commonly used error type is called root mean square error, or RMSE in short. RMSE takes a difference between the predicted and actual values, squares it, and takes the mean of that, and then takes a root of it. It is quite biased towards huge errors and thus suited for dataset which follow a normal bell like distribution with few outliers. 

### Underfitting And Overfitting

When the prediction model builds itself very close to the training data, so and so that the predicted data gets effected a lot with a high MAE, the model is said to be overfitted.

On the other hand, when the training error itself is very high, we can say that the model hasn't taken most of the features of the training data, thus it can't predict well.

In short,

* **Underfitting:** Training MSE is very high.
* **Overfitting:** Training MSE low, predicted MSE very high. 

### Optimizing The Model

One of the parameters we can use to optimize the decision tree model is `max_leaf_nodes`, which says how many leaf nodes (the end node) the tree can have. We can build a for loop supplying various sizes to this and noting the number that produces the least MAE. 

```python
from sklearn.metrics import mean_absolute_error
from sklearn.tree import DecisionTreeRegressor

def get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y):
    model = DecisionTreeRegressor(max_leaf_nodes=max_leaf_nodes, random_state=0)
    model.fit(train_X, train_y)
    preds_val = model.predict(val_X)
    mae = mean_absolute_error(val_y, preds_val)
    return(mae)
	
for max_leaf_nodes in [5, 50, 500, 5000]:
    my_mae = get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y)
    print("Max leaf nodes: %d Mean Absolute Error:  %d" %(max_leaf_nodes, my_mae))
```

### Using Another Model

You can often increase the accuracy by entirely using another model. For our example, we use the Random Forest model which is like Decision Tree, except the leafs are way more better pronounced and usually is much more accurate for the same dataset.

```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error

forest_model = RandomForestRegressor(random_state=1)
forest_model.fit(train_X, train_y)
melb_preds = forest_model.predict(val_X)
print(mean_absolute_error(val_y, melb_preds))
```

You can test this and see if its better than the Decision Tree that you used above by comparing the MAE. 