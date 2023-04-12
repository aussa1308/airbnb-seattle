# Exploring the Seattle Airbnb Landscape

This repository contains code that analyzes Airbnb booking data in Seattle, WA, and uses logistic regression to predict whether a listing is booked or not. The analysis includes data cleaning, feature engineering, and model training and evaluation.

## Dataset

The dataset used in this analysis is the Seattle Airbnb Data. It contains information about Airbnb listings that consists of three files:

- `listings.csv`: Detailed information about each listing, such as property type, price, location, and more.
- `calendar.csv`: Availability and price information for each listing on a daily basis.
- `reviews.csv`: Detailed reviews left by guests for each listing.

## Functions
**generate_booking_trend(calendar)**
This function generates a booking trend graph for an Airbnb property in Seattle.

Input:

calendar (pandas dataframe): A dataframe with a column named "available" indicating the availability of the property on each date.
Output:

A line graph of the booking trend over time.

**plot_top_neighborhoods(listing, calendar)**
This function returns a horizontal bar chart of the top 30 Airbnb booking neighborhoods in Seattle.

Input:

listing (pandas dataframe): A dataframe of Airbnb listings that includes the columns 'id' and 'neighbourhood'.
calendar (pandas dataframe): A dataframe of Airbnb booking data that includes the columns 'listing_id' and 'booked'.
Output:

None. Displays a horizontal bar chart of the top 30 Airbnb booking neighborhoods in Seattle.

Note: This code assumes that the calendar dataframe contains a column named "available" indicating the availability of the property on each date, and that the listing dataframe contains columns named "id" and "neighbourhood".

**clean_data(raw_data)**
The clean_data() function takes a raw dataframe as input and performs the following cleaning steps:

Removes rows with missing values in the "available" column.
Creates a binary "booked" column based on the "available" column.
Creates binary columns indicating whether the "calendar_updated", "cleaning_fee", and "amenities" columns are null or not.
Converts the "price" and "host_response_rate" columns to float and removes percent and dollar signs.
Drops unnecessary columns.
Fills missing values in numeric columns with the column mean.
Converts categorical variables to binary variables using one-hot encoding.
Input:

raw_data (pandas dataframe): A dataframe with raw Airbnb booking data.
Output:

The cleaned X and y variables.

**coef_weights(model, X_train)**
The coef_weights() function takes the coefficients of the logistic regression model and the X_train dataframe as input, and returns a dataframe with the features and their corresponding coefficients sorted in ascending order of absolute coefficients.

Input:

model (logistic regression model): A trained logistic regression model.
X_train (pandas dataframe): A dataframe containing the features used to train the logistic regression model.
Output:

A dataframe with the features and their corresponding coefficients sorted in ascending order of absolute coefficients.

**plot_top_coef_features(weights)**
The plot_top_coef_features() function takes the output dataframe of the coef_weights() function as input and plots the 15 features with the highest coefficients. The plot shows the coefficient values of each feature and has a title, x-label, y-label, and legend removed.

Input:

weights (pandas dataframe): A dataframe with the features and their corresponding coefficients sorted in ascending order of absolute coefficients.
Output:

None. Displays a plot of the 15 features with the highest coefficients.

**Model Training and Evaluation**
The cleaned X and y variables are split into training and testing sets using the train_test_split() function. The logistic regression model is created using the LogisticRegression() class with a max_iter parameter of 3. The model is then trained on the training data using the fit() method. The trained model is used to make predictions on the test data using the predict() method. The accuracy of the model is evaluated using the `

## Medium Post

For a more explanation of the analysis, you can read the Medium post at: https://medium.com/@aussa.tris/exploring-the-seattle-airbnb-landscape-67b5aa639b8
