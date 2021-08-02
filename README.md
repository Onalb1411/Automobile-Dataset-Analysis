# Automobile-Dataset-Analysis
This data science project focuses on the analysis of Automobile data set from cognitiveclasses.ai. This project is done as part of the *Data Analysis with Python* course path. You can find the "Automobile Dataset" <a href = "https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data." target = "_blank"> here </a> 

***
## Data Wrangling procedures

### 1. Handle missing values
* Convert "?" to NaN -- In the car dataset, missing data comes with the question mark "?". To dela with this, I replaced the "?" with NaN (Not a Number) in the dataset
* Evaluating for Missing Data -- Here, I checked wether there were any anymore missing data
* Count missing values in each column -- Using a for loop in Python, I counted the number of null values in each column. Alternatively, i also used the isnull().sum() function

#### 1.1 Deal with missing data
In this section, i explain how i handles the missing data and justify the reasons for handling data in the way it was done.

##### 1.1.1 Drop data:
* Drop the whole row -- since "price" had 4 missing values, I simply deleted the whole row because price is what we want to predict. Any data entry without price data cannot be used for prediction; therefore any row now without price data is not useful to us

##### 1.1.2 Replace data
###### Replace it by mean:
Here, i replaced the missing data with the average of the column. Below columns were replaced with average values;
* "normalized-losses": 41 missing data, "stroke": 4 missing data, "bore": 4 missing data, "horsepower": 2 missing data, "peak-rpm": 2 missing data

##### Replace it by frequency
* I replaced "num-of-doors" which has 2 missing data, with "four". -- Reason being : 84% sedans is four doors. Since four doors is most frequent, it is most likely to occur
                                     
### 2. Correct data format: 
Here, I ensured that the data columns are in there correct data types before performing further analysis. The procedure i followed was:

* list the data types for each column
* Convert data types to proper format
        * bore,stroke, price and peak-prm to float
        * normalised losses to integer
* list the columns after the conversion
        
### 3. Standardize data
 * `Standardization` is the process of transforming data into a common format, allowing for meaningful comparison. In my dataset, the fuel consumption columns "city-mpg" and "highway-mpg" are represented by mpg (miles per gallon) unit. Assume we are developing an application in a country that accepts the fuel consumption with L/100km standard. We will need to apply data transformation to transform mpg into L/100km. The formula for unit conversion is: L/100km = 235 / mpg
        
### 4. Normalize data
* `Normalization` is the process of transforming values of several variables into a similar range
*  I, for example, scaled the columns "length", "width" and "height". I normalized these variables so their value ranges from 0 to 1. Approach: replace original value by (original value)/(maximum value)        
        
### 5. Binning
* `Binning` is a process of transforming continuous numerical variables into discrete categorical 'bins' for grouped analysis.
* Example: --> In my dataset, "horsepower" is a real valued variable ranging from 48 to 288 and it has **57** unique values. What if we only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? Can we rearrange them into three ‘bins' to simplify analysis?
        I used the pandas method 'cut' to segment the 'horsepower' column into 3 bins.
* Bins Visualization - Here, i visualized the bins created above to see there distributions
        
### 6. Indicator Variable (or Dummy Variable)
We use indicator variables so we can use categorical variables for regression analysis in the later modules. The column "fuel-type" has two unique values: "gas" or "diesel". Regression doesn't understand words, only numbers. To use this attribute in regression analysis, we convert "fuel-type" to indicator variables.

***

## Exploratory Data Analysis 
The main objective here was to Explore features or charecteristics to predict price of car
### 1. Import Data from Module
Here we do the basic importing from the clead data set ie cleandf.csv

### 2. Analyzing Individual Feature Patterns using Visualization
* Quiz -- Find the correlation between the following columns: bore, stroke, compression-ratio, and horsepower.

#### Positive Linear Relationship
* Let's find the scatterplot of "engine-size" and "price".
* We can examine the correlation between 'engine-size' and 'price' and see that it's approximately 0.87.
* Highway mpg is a potential predictor variable of price. Let's find the scatterplot of "highway-mpg" and "price".
* We can examine the correlation between 'highway-mpg' and 'price' and see it's approximately -0.704.
#### Weak Linear Relationship
* Let's see if "peak-rpm" is a predictor variable of "price".
* We can examine the correlation between 'peak-rpm' and 'price' and see it's approximately -0.101616.
* Find the correlation between x="stroke" and y="price".

#### Categorical Variables
* Let's look at the relationship between "body-style" and "price".
* Let's examine engine "engine-location" and "price":
* Let's examine "drive-wheels" and "price".

### 3. Descriptive Statistical Analysis
* Let's first take a look at the variables by utilizing a description method
### 4. Basics of Grouping
* let's group by the variable "drive-wheels". 
### 5. Correlation and Causation
### 6. ANOVA
***
