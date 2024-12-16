# IBM-Data-Science-Capstone-SpaceX

This project summarizes the work that has been done during the [IBM Data Science Professional Certificate](https://www.coursera.org/professional-certificates/ibm-data-science) specialization.

## Background
SpaceX, a leader in the commercial space industry, is revolutionizing space travel by making it more affordable and accessible. Its achievements include sending spacecraft to the International Space Station, launching a satellite constellation to provide internet access, and conducting manned space missions. Central to SpaceX's success is its innovative reuse of the first stage of its Falcon 9 rocket, which reduces launch costs to $62 million, compared to upwards of $165 million charged by other providers who cannot reuse this component.

This cost advantage underscores the importance of determining whether the first stage of a rocket can be reused, as it directly impacts the affordability of a launch. Using public data and machine learning models, we aim to predict the likelihood of the first stage successfully landing and being reused, which can inform the pricing and feasibility of launches for SpaceX and its competitors.

## Explore
* How variables such as payload mass, launch site, number of flights, and orbits affect the success of first-stage Falcon 9 landing
* The rate of successful landings over the years
* Best predictive model for successful landings (binary classification)

## Executive Summary
The research attempts to identify the factors for a successful rocket landing. To make this determination, the following methodologies were used:

* Collect data using SpaceX REST API and web scraping techniques from a wiki page
* Wrangle data to create success / fail outcome variable
* Explore data with data visualization techniques, considering the following factors: payload, launch site, flight number, and yearly trend
* Analyze the data with SQL, calculating the following statistics: total payload, payload range for successful launches, and total number of successful and failed outcomes
* Explore launch site success rates and proximity to geographical markers
* Visualize the launch sites with the most success and successful payload ranges
* Build Models to predict landing outcomes using Logistic Regression, Support Vector Machine (SVM), Decision Tree, and K-Nearest Neighbour (KNN)

## Results
### Exploratory Data Analysis:
* Launch success has improved over time
* KSC LC-39A has the highest success rate among landing sites
* Orbits ES-L1, GEO, HEO, and SSO have a 100% success rate

### Visualization / Analytics:
* Most launch sites are near the equator, and all are close to the coast

### Predictive Analytics
* All models performed similarly on the test set. The decision tree model slightly outperformed when looking at .best_score_

## Methodology
### Data Collection - API
* Request data from SpaceX API (rocket launch data) through a REST API
* Decode response using .json() and convert to a DataFrame using .json_normalize()
* Request information about the launches from SpaceX API using custom functions
* Create Dictionary from the data
* Create DataFrame from the dictionary
* Filter DataFrame to contain only Falcon 9 launches
* Replace missing values of Payload Mass with calculated .mean()
* Export data to .csv file

### Data Collection - Web Scraping
* Request data (Falcon 9 launch data) from Wikipedia
* Create BeautifulSoup object from HTML response
* Extract column names from HTML table header
* Collect data from parsing HTML tables
* Create Dictionary from the data
* Create DataFrame from the dictionary
* Export data to .csv file

### Data Wrangling
* Convert outcomes into 1 for a successful landing and 0 for an unsuccessful landing

### EDA with Visualization
* Create charts to analyze relationships and show comparisons

### EDA with SQL
* Query the data to understand more about the data

### Maps with Folium
* Create maps to visualize launch sites, view launch outcomes and see distance to proximities

### Dashboard with Plotly Dash
* Create dashboard
* Pie chart showing successful launches
* Scatter chart showing Payload Mass vs. Success Rate by Booster Version

### Predictive Analytics
* Create a NumPy array from the Class column
* Standardize the data with StandardScaler. Fit and transform the data.
* Split the data using train_test_split
* Create a GridSearchCV object with cv=10 for parameter optimization
* Apply GridSearchCV on different algorithms: logistic regression (LogisticRegression()), support vector machine (SVC()), decision tree (DecisionTreeClassifier()), K-Nearest Neighbor (KNeighborsClassifier())
* Calculate accuracy on the test data using .score() for all models
* Assess the confusion matrix for all models
* Identify the best model using Jaccard_Score, F1_Score and Accuracy

## Conclusion
* Model Performance: The models performed similarly on the test set with the decision tree model slightly outperforming
* Equator: Most of the launch sites are near the equator for an additional natural boost - due to the rotational speed of earth - which helps save the cost of putting in extra fuel and boosters
* Coast: All the launch sites are close to the coast
Launch Success: Increases over time
* KSC LC-39A: Has the highest success rate among launch sites. Has a 100% success rate for launches less than 5,500 kg
* Orbits: ES-L1, GEO, HEO, and SSO have a 100% success rate
* Payload Mass: Across all launch sites, the higher the payload mass (kg), the higher the success rate

## Additional Things to Consider
* Dataset: A larger dataset will help build on the predictive analytics results to help understand if the findings can be generalizable to a larger data set
* Feature Analysis / PCA: Additional feature analysis or principal component analysis should be conducted to see if it can help improve accuracy
*XGBoost: It's a powerful model that was not utilized in this study. It would be interesting to see if it outperforms the other classification models
