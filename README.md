<h1> Taxi-Tip-Prediction </h1>
The aim of this project was to predict taxi tips in New York City using machine learning models. By accurately predicting the tip amount and categorizing it into 'high', 'medium', and 'low', we aim to provide insights that could help taxi services enhance customer satisfaction and optimize tip-related strategies.The dataset used for this analysis is publicly available here.  [here](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

<h2> Data Understanding </h2>
The dataset used was the TLC Yellow Taxi Trip Records of June 2019, publicly available from the Taxi & Limousine Commission (TLC), City of New York. The raw data included columns such as 'VendorID', 'tpep_pickup_datetime', 'tpep_dropoff_datetime', 'passenger_count', 'trip_distance', 'RatecodeID', 'store_and_fwd_flag', 'PULocationID', 'DOLocationID', 'payment_type', 'fare_amount', 'extra', 'mta_tax', 'tip_amount', 'tolls_amount', 'improvement_surcharge', 'total_amount', and 'congestion_surcharge'.

<h2> Data Preparation </h2>
<b>Input:</b> Raw taxi trip data.
<p><b>Process:</b></p>
<ul>
<li> Clean the data by removing rows with zero tips, tips larger than fare costs, and unusually high fare costs.</li>
<li> Drop the 'total_amount' column to avoid data leakage.</li>
<li> Feature engineering: extract pickup and dropoff hours, categorize features such as "VendorID", "RatecodeID", "pickup_hour", and "dropoff_hour".</li>
<li> Data cleaning involved removing rows with zero tip amounts, tips larger than fare costs, and trips with unusually high fare costs. The 'total_amount' column was dropped to avoid data leakage. Feature engineering included extracting relevant features like pickup and dropoff hours and categorizing features such as "VendorID", "RatecodeID", "pickup_hour", and "dropoff_hour". Correlation analysis identified trip distance as the most significant positive predictor of tip amount.</li>
<li>Correlation analysis was performed to understand how different factors affect the tip amount:Trip Distance: Highest positive correlation with tip amount (0.8), indicating longer trips tend to receive higher tips;Congestion Surcharge: Highest negative correlation with tip amount (-0.2), indicating that trips with a congestion surcharge tend to receive lower tips.</li>
</ul>
<b>Output:</b> A cleaned and processed dataset ready for modeling, with relevant features and target variables.
<p>Minimum amount value is  0.01
Maximum amount value is  130.0
90% of the trips have a tip amount less or equal than  5.95</p>

<h2> Modelling </h2>
<p><b>Input:</b> Prepared dataset with cleaned and engineered features.</p>
<p><b>Process:</b></p>
<p>Two main types of models were developed:</p>
<p><b>Decision Tree Regressor:</b>The model was trained to predict the exact tip amount. </p>
<p><b>Classification Models:</b></p>
<p><b>Logistic Regression and Random Forest Classifier:</b>A comparsion method was used to determine the probability of the predicted tips falling into 'low', 'medium', or 'high' categories.</p>

<b>Output:</b>Candle plots visualized the predicted ranges for each tip category.The candle plot visualization provided a clear comparison of the predicted tip categories' ranges for both logistic regression and random forest models. It highlighted the logistic regression model's broader range of predictions compared to the random forest model's tighter and more precise predictions. This further supports the idea that the random forest model might be overfitting.

<h2> Evaluation </h2>
<p>Model performance was evaluated using several metrics and visualization techniques:</p>
<p><b>Decision Tree Regressor:</b> The Decision Tree Regressor demonstrated a reasonable performance with a mean squared error (MSE) of 1.689 and an R-squared value of 0.76746. This suggests that the model captures about 76.75% of the variance in the tip amounts. The density plot comparison indicates that the model's predictions closely follow the actual values, though there may be room for improvement in handling more complex relationships.</p>
<p><b>Logistic Regression:</b> The logistic regression model achieved an overall accuracy of 63% with varying performance across different tip categories. The F1-scores indicate that the model performs best for the 'high' tip category, with an F1-score of 0.74, followed by the 'low' category (0.65) and the 'medium' category the predicted tips falling into 'low', 'medium', or 'high' categories:y (0.47). This suggests that the model may struggle more with predicting 'medium' tips, which could be due to the overlapping nature of this category with the others.</p>
<p><b>Random Forest:</b> The random forest model showed perfect performance with an accuracy, precision, recall, and F1-score of 1.00 across all categories. While this indicates an excellent fit to the training data, it raises concerns about overfitting. The model might not generalize well to new, unseen data, despite its high performance on the test set.</p>

<h2> Conclusion </h2>
<p>The combination of regression trees for precise tip amount predictions and logistic regression for categorizing tips into low, medium, and high categories is a robust approach. It leverages the strengths of both model types, providing detailed numerical predictions and broad categorical insights. However, care must be taken to ensure models do not overfit and are validated on diverse datasets to ensure their reliability and applicability in real-world scenarios.</p>
