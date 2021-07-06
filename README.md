# Automobile-Dataset-Analysis
This data science project focuses on the analysis of Automobile data set from cognitive classes.You can find the "Automobile Dataset" from <a href = "https://archive.ics.uci.edu/ml/machine-learning-databases/autos/imports-85.data." target = "_blank"> here </a> 

***
## Data Wrangling procedures

### 1. Handle missing values
* Convert "?" to NaN -- In the car dataset, missing data comes with the question mark "?". i replaced the "?" with NaN (Not a Number)
* Evaluating for Missing Data -- check wether there are anymore missing data
* Count missing values in each column -- Using a for loop in Python, i counted the number of null values in each column. Alternatively, i also used the isnull().sum() function

#### 1.1 Deal with missing data

##### 1.1.1 Drop data:
* Drop the whole row -- "price": 4 missing data, simply delete the whole row -- Reason: price is what we want to predict. Any data entry without price data cannot be used for prediction; therefore any row now without price data is not useful to us
* Drop the whole column

##### 1.1.2 Replace data
###### Replace it by mean:
* "normalized-losses": 41 missing data, replace them with mean
* "stroke": 4 missing data, replace them with mean
* "bore": 4 missing data, replace them with mean
* "horsepower": 2 missing data, replace them with mean
* "peak-rpm": 2 missing data, replace them with mean
##### Replace it by frequency
* "num-of-doors": 2 missing data, replace them with "four". -- Reason: 84% sedans is four doors. Since four doors is most frequent, it is most likely to occur
                                     
### 2. Correct data format: 
* list the data types for each column
* Convert data types to proper format
        * bore,stroke, price and peak-prm to float
        * normalised losses to integer
* list the columns after the conversion
        
### 3. Standardize data
 * `Standardization` is the process of transforming data into a common format, allowing for meaningful comparison. In our dataset, the fuel consumption columns "city-mpg" and "highway-mpg" are represented by mpg (miles per gallon) unit. Assume we are developing an application in a country that accepts the fuel consumption with L/100km standard.
* We will need to apply data transformation to transform mpg into L/100km. 
* The formula for unit conversion is: L/100km = 235 / mpg
        
### 4. Normalize data
* `Normalization` is the process of transforming values of several variables into a similar range
*  we scale the columns "length", "width" and "height".
        * Target: would like to normalize those variables so their value ranges from 0 to 1
        * Approach: replace original value by (original value)/(maximum value)        
        
### 5. Binning
* `Binning` is a process of transforming continuous numerical variables into discrete categorical 'bins' for grouped analysis.
* Example: --> In our dataset, "horsepower" is a real valued variable ranging from 48 to 288 and it has 57 unique values. What if we only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? Can we rearrange them into three ‘bins' to simplify analysis?
        We will use the pandas method 'cut' to segment the 'horsepower' column into 3 bins.
* Bins Visualization
        
### 6. Indicator Variable (or Dummy Variable)
We use indicator variables so we can use categorical variables for regression analysis in the later modules. We see the column "fuel-type" has two unique values: "gas" or "diesel". Regression doesn't understand words, only numbers. To use this attribute in regression analysis, we convert "fuel-type" to indicator variables.

***
