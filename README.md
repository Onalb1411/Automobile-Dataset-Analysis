# Automobile-Dataset-Analysis
This data science project focuses on the analysis of Automobile data set from cognitive classes.
## Data Wrangling procedures
Objectives:
    * Handle missing values
        Convert "?" to NaN -- In the car dataset, missing data comes with the question mark "?". We replace "?" with NaN (Not a Number)

        Evaluating for Missing Data -- check wether there are anymore missing data

        Count missing values in each column -- Using a for loop in Python, we can quickly figure out the number of missing values in each column.

        Deal with missing data
            How to deal with missing data?
                Drop data
                    a. Drop the whole row
                    b. Drop the whole column
                Replace data
                    a. Replace it by mean
                    b. Replace it by frequency
                    c. Replace it based on other functions

            Whole columns should be dropped only if most entries in the column are empty
            In our dataset, none of the columns are empty enough to drop entirely. We have some freedom in choosing which method to replace data; however, some methods may seem more reasonable than others. We will apply each method to many different columns:
                * Replace by mean:
                    * "normalized-losses": 41 missing data, replace them with mean
                    * "stroke": 4 missing data, replace them with mean
                    * "bore": 4 missing data, replace them with mean
                    * "horsepower": 2 missing data, replace them with mean
                    * "peak-rpm": 2 missing data, replace them with mean
                * Replace by frequency:
                    * "num-of-doors": 2 missing data, replace them with "four". -- Reason: 84% sedans is four doors. Since four doors is most frequent, it is most likely to occur
                * Drop the whole row:
                    * "price": 4 missing data, simply delete the whole row -- Reason: price is what we want to predict. Any data entry without price data cannot be used for prediction; therefore any row now without price data is not useful to us
    * Correct data format
        * list the data types for each column
        * Convert data types to proper format
        * list the columns after the conversion
    * Standardize data
        --> *Standardization* is the process of transforming data into a common format, allowing the researcher to make the meaningful comparison.
        In our dataset, the fuel consumption columns "city-mpg" and "highway-mpg" are represented by mpg (miles per gallon) unit. Assume we are developing an application in a country that accepts the fuel consumption with L/100km standard.
        We will need to apply data transformation to transform mpg into L/100km. The formula for unit conversion is:
        L/100km = 235 / mpg
    * Normalize data
        Normalization is the process of transforming values of several variables into a similar range
        To demonstrate normalization, let's say we want to scale the columns "length", "width" and "height".

        Target: would like to normalize those variables so their value ranges from 0 to 1

        Approach: replace original value by (original value)/(maximum value)    
    
    * Binning
        Binning is a process of transforming continuous numerical variables into discrete categorical 'bins' for grouped analysis.
        Example:
        In our dataset, "horsepower" is a real valued variable ranging from 48 to 288 and it has 57 unique values. What if we only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? Can we rearrange them into three ‘bins' to simplify analysis?

        We will use the pandas method 'cut' to segment the 'horsepower' column into 3 bins.
        * Bins Visualization
    * Indicator Variable (or Dummy Variable)
        We use indicator variables so we can use categorical variables for regression analysis in the later modules.
        We see the column "fuel-type" has two unique values: "gas" or "diesel". Regression doesn't understand words, only numbers. To use this attribute in regression analysis, we convert "fuel-type" to indicator variables.

