# bba-ai-ml-portfolio
Data Preparation and Supervised Machine Learning
Learning Outcomes
After completing this module, students will be able to:
Identify common data-quality problems.
Explain data preprocessing and feature engineering.
Differentiate between classification and regression.
Explain training data, testing data, features and target variables.
Understand Logistic Regression, Decision Tree and Random Forest conceptually.
Interpret Accuracy, Precision, Recall, F1-score and a Confusion Matrix.
Build and compare classification models using Orange Data Mining without coding.
Translate model results into a business recommendation.
Add the completed model workflow and supporting evidence to GitHub.

1. Why Data Quality Matters
An AI or Machine Learning model learns from the data provided to it. If the data is incorrect, incomplete or biased, the model may also produce unreliable results.
Simple Analogy
Preparing data for Machine Learning is similar to preparing ingredients before cooking.
Missing ingredients affect the final dish.
Incorrect quantities produce poor results.
Spoiled ingredients cannot produce good food.
Using irrelevant ingredients creates confusion.
The same principle applies to AI:
Poor-Quality Data → Poor Learning → Unreliable Predictions
This is commonly expressed as:
Garbage In, Garbage Out

2. Common Data-Quality Problems
Missing Values
A missing value means that some required information is unavailable.
Customer_ID
Monthly_Spending
Complaints
C101
2500
0
C102


3

The monthly spending for customer C102 is missing.
Possible Reasons
The customer did not provide the information.
The system failed to record it.
Different databases were combined.
The value was entered incorrectly.

Duplicate Records
A duplicate occurs when the same observation appears more than once.
Customer_ID
Monthly_Spending
C101
2500
C101
2500

Duplicates can produce incorrect totals and may give too much importance to repeated records.

Incorrect Values
Examples include:
Age entered as 220
Salary entered as -35000
Delivery distance entered as 5000 km for a local order
Customer category entered as both Premium and Premimum

Inconsistent Formats
The same information may be written differently.
Examples:
Delhi
delhi
NEW DELHI
New Delhi
Other examples:
Yes, Y, True, 1
No, N, False, 0
These values may represent the same category but appear different to a computer.

Outliers
An outlier is a value that is very different from most other values.
Example:
Customer
Monthly Spending
A
₹2,000
B
₹2,500
C
₹2,200
D
₹95,000

Customer D may be:
A genuine high-value customer
A corporate customer
A data-entry error
A fraudulent transaction
An outlier should be investigated before it is removed.

Irrelevant Data
Some columns may not help solve the business problem.
For predicting customer churn, the following may be irrelevant:
Random serial number
Customer’s favourite colour
Report-printing date
Employee who entered the record
Removing irrelevant information may make the dataset easier to understand and use.

Biased Data
A dataset is biased when it does not fairly represent the real population or when past decisions contain unfair patterns.
Example
If a recruitment model is trained only on records of previously selected candidates, it may learn the organization’s historical preferences rather than identify all qualified candidates fairly.

Outdated Data
Old data may no longer represent current customer behaviour, prices, business processes or market conditions.
Example
Customer behaviour recorded before the widespread use of digital payments may not accurately represent current purchasing patterns.

3. Data Preprocessing
Data preprocessing means preparing raw data before it is used for analysis or Machine Learning.
Typical preprocessing activities include:
Removing duplicate records
Correcting inconsistent formats
Handling missing values
Investigating outliers
Selecting relevant columns
Converting data into a suitable format
Scaling numerical variables when required
Protecting or removing personal identifiers
Data Preprocessing Flow
Raw Data
→ Inspect Data
→ Correct Errors
→ Handle Missing Values
→ Remove Duplicates
→ Standardize Formats
→ Select Relevant Features
→ Prepare Data for Modelling

4. Handling Missing Values
Missing values should not be filled randomly.
Possible approaches include:
Remove the Record
Suitable when:
Very few records are affected.
The missing record is not important.
Removing it will not create bias.
Remove the Column
Suitable when:
Most values in the column are missing.
The column is not important to the business problem.
Fill with a Typical Value
Examples:
Numerical data: mean or median
Categorical data: most frequent category MODE
Create an “Unknown” Category
This may be useful when the absence of information itself is meaningful.
The method selected should be explained and documented.

5. Feature Selection
Feature selection means choosing the existing variables that are most useful for solving the business problem.
For customer churn prediction:
Potentially Useful Features
Monthly spending
Number of complaints
App visits
Membership duration
Days since last purchase
Potentially Unhelpful Feature
Customer ID
Customer_ID is necessary for identifying the customer, but it normally does not explain why the customer may leave.
Simple Analogy
A doctor does not use every available fact about a patient to diagnose every illness. The doctor selects symptoms and test results relevant to the medical problem.
Similarly, an ML model should use relevant business features.

6. Feature Engineering
Feature engineering means creating a new, useful feature from existing data.
Example 1: Customer Engagement
Existing features:
App visits
Purchases
Reviews
Possible new feature:
Customer Engagement Score
Example 2: Employee Experience
Existing feature:
Joining Date
Possible new feature:
Months in Organization
Example 3: Finance
Existing features:
Monthly income
Monthly debt payment
Possible new feature:
Debt-to-Income Ratio
Example 4: Logistics
Existing features:
Order time
Delivery time
Possible new feature:
Total Delivery Duration
Feature Selection vs Feature Engineering
Feature Selection
Feature Engineering
Selects useful existing features
Creates new features
Removes irrelevant information
Combines or transforms information
Example: selecting complaints
Example: complaints per month
Example: selecting income
Example: debt-to-income ratio


7. What Is Supervised Learning?
Supervised Learning is a type of Machine Learning in which the model learns from examples containing both input features and the correct answer.
Simple Analogy
Supervised Learning is like learning with an answer key.
The student receives:
A question
The correct answer
Feedback
After studying several solved examples, the student attempts a new question.
Machine Learning Example
Monthly Spending
Complaints
App Visits
Churn
2500
0
12
No
1100
3
4
Yes
3200
0
15
No
900
4
3
Yes


Monthly Spending, Complaints and App Visits are features.
Churn is the known answer or target.
The model learns from these labelled examples.

8. Two Main Types of Supervised Learning
Classification
Classification predicts a category or class.
Examples
Business Problem
Predicted Category
Will a customer leave?
Yes or No
Is a transaction suspicious?
Fraud or Not Fraud
Will an employee leave?
Leave or Stay
Will a delivery be delayed?
Delayed or On Time
What is the customer sentiment?
Positive, Neutral or Negative

Easy Test
If the expected answer is a label or category, the problem is usually classification.

Regression
Regression predicts a numerical value.
Examples
Business Problem
Predicted Number
What will next month’s sales be?
₹8,50,000
How much will a customer spend?
₹3,200
How long will delivery take?
42 minutes
What will the product demand be?
1,500 units
What may a house cost?
₹75 lakh

Easy Test
If the expected answer is an amount, quantity, price or time, the problem is usually regression.

9. Classification vs Regression
Classification
Regression
Predicts a category
Predicts a number
Churn: Yes or No
Future sales: ₹8,50,000
Fraud or Not Fraud
Expected loss: ₹25,000
High, Medium or Low Risk
Delivery time: 42 minutes
Suitable for label-based outcomes
Suitable for continuous numerical outcomes


10. Training Data and Testing Data
A model should not be evaluated only on the examples it has already studied.
Training Data
Training data is used by the model to learn patterns.
Testing Data
Testing data is used to check how well the model performs on unseen examples.
Simple Analogy
Training data: Questions practised before an examination
Testing data: New questions presented in the examination
If a student only repeats memorized answers but cannot solve new questions, real learning has not occurred.
The same principle applies to Machine Learning.
Dataset
├── Training Data → Used to learn
└── Testing Data → Used to evaluate

11. Machine Learning Model
A Machine Learning model is the learned pattern or decision system created after an algorithm studies training data.
Algorithm vs Model
Algorithm: The learning method
Model: The result created after learning from data
Simple Analogy
A recipe is like an algorithm.
The prepared dish is like a model.

12. Classification Algorithms
Logistic Regression
Despite its name, Logistic Regression is commonly used for classification.
It estimates the probability of a category.
Example
Probability of Customer Churn = 0.82
This may be interpreted as an 82% estimated probability of churn.
Suitable For
Yes/No outcomes
Probability-based predictions
Interpretable business problems

Decision Tree
A Decision Tree makes decisions through a sequence of questions.
Example
Are complaints greater than 2?
├── Yes → Are app visits fewer than 5?
│   ├── Yes → High Churn Risk
│   └── No → Medium Churn Risk
└── No → Low Churn Risk
Simple Analogy
A Decision Tree is similar to a flowchart used by a manager.
Advantage
It is relatively easy to explain.
Limitation
A very large tree may memorize the training data and perform poorly on new data.

Random Forest
A Random Forest combines the decisions of multiple Decision Trees.
Each tree produces a prediction, and the final result is based on their combined decision.
Simple Analogy
Decision Tree: Asking one manager
Random Forest: Asking a committee of managers and using the combined opinion
Advantage
It can produce better predictions than a single tree.
Limitation
It is more difficult to explain than one small Decision Tree.

13. Model Evaluation
A model should not be selected only because it produces a prediction. Its predictions must be evaluated.
For classification, common measures include:
Confusion Matrix
Accuracy
Precision
Recall
F1-score

14. Confusion Matrix
A Confusion Matrix compares actual outcomes with model predictions.
Consider a fraud-detection model.


Predicted Fraud
Predicted Genuine
Actual Fraud
True Positive
False Negative
Actual Genuine
False Positive
True Negative

True Positive
The transaction was fraudulent, and the model correctly identified it as fraud.
True Negative
The transaction was genuine, and the model correctly identified it as genuine.
False Positive
The transaction was genuine, but the model incorrectly flagged it as fraud.
Business Impact
Genuine customer may be inconvenienced.
Transaction may be delayed.
Customer trust may be affected.
False Negative
The transaction was fraudulent, but the model incorrectly classified it as genuine.
Business Impact
Fraud may remain undetected.
The organization may lose money.
Customer or organizational security may be affected.

15. Accuracy
Accuracy measures the proportion of total predictions that were correct.
Accuracy = Correct Predictions ÷ Total Predictions
Example
If 90 out of 100 predictions are correct:
Accuracy = 90%
Limitation of Accuracy
Suppose only two out of 100 transactions are fraudulent.
A model predicts that all 100 transactions are genuine.
It correctly predicts 98 genuine transactions.
Its accuracy is 98%.
However, it misses every fraudulent transaction.
Therefore:
High accuracy does not always mean that the model is useful.

16. Precision
Precision answers: When the model predicted “positive,” how often was it correct?
In fraud detection:
Of all transactions flagged as fraud, how many were actually fraudulent?
High precision is important when a false alarm is costly.
Examples
Incorrectly blocking genuine financial transactions
Incorrectly rejecting qualified candidates
Sending an expensive offer to unsuitable customers

17. Recall
Recall answers: Of all actual positive cases, how many did the model identify?
In fraud detection:
Of all actual fraudulent transactions, how many were detected?
High recall is important when missing a positive case is dangerous or expensive.
Examples
Missing a fraudulent transaction
Missing a serious medical condition
Missing a high-risk safety incident
Failing to identify a customer likely to leave

18. F1-Score
F1-score provides a balance between Precision and Recall.
It is useful when:
Both false positives and false negatives matter.
The classes are not evenly distributed.
Accuracy alone may be misleading.
Students do not need to calculate the F1-score manually at this stage. They should understand what it represents.

19. Choosing the Appropriate Metric
Business Situation
Important Metric
Reason
General balanced classification
Accuracy
Overall correctness matters
Expensive retention offer
Precision
Avoid targeting too many low-risk customers
Fraud detection
Recall
Missing fraud can be costly
Disease screening
Recall
Missing a positive case can be dangerous
Both errors matter
F1-score
Balances Precision and Recall

The best metric depends on the business objective and the cost of each type of error.

Practical Project: No-Code Customer Churn Prediction
Project Objective
Build and compare classification models that predict whether a telecom customer may leave the company.
Students will:
Load a real business dataset.
Inspect data types and quality.
Select relevant features.
Apply preprocessing.
Build three classification models.
Evaluate the models.
Interpret a Confusion Matrix.
Recommend a model from a business perspective.
Save the workflow and upload evidence to GitHub.

Tool: Orange Data Mining
Orange is an open-source visual Machine Learning and data-visualization platform. Students build workflows by dragging, dropping and connecting widgets. No programming is required.
Official Download
Download Orange Data Mining
The current official release available on the download page is Orange 3.40.0. Orange also provides a portable Windows version that can be extracted and opened without a traditional installation. Always use the version currently shown on the official page if a newer release appears.

Installing Orange on Windows
Standard Installation
Open the official Orange download page.
Under Windows, select the standalone installer.
Wait for the .exe file to download.
Open the downloaded file.
Allow the installation to proceed.
Use the default installation options.
Launch Orange after installation.
The standalone installer can normally be used without administrator privileges.
Portable Option
If installation is restricted:
Download Portable Orange from the same page.
Extract the downloaded ZIP file.
Open the extracted folder.
Launch the Orange shortcut.
macOS
Select the version matching the Mac processor:
Apple silicon
Intel
To check the processor:
Select the Apple menu.
Open About This Mac.
Check the Chip or Processor field.

Understanding the Orange Interface
The Orange interface contains:
Widget panel: Tools arranged by category
Canvas: Area where the workflow is created
Connections: Lines that transfer data between widgets
Widget window: Settings and results for the selected widget
Important Widget Categories
Category
Purpose
Data
Load and inspect datasets
Transform
Clean and prepare data
Visualize
Create charts and plots
Model
Add Machine Learning algorithms
Evaluate
Compare and assess models


Create the Project Folder
Create this folder on the computer:
telecom-churn-no-code-ml
Create the following subfolders:
telecom-churn-no-code-ml/
├── workflow/
├── results/
├── screenshots/
└── report/

Load the Telecom Churn Dataset
Method 1: Use the Built-In Dataset
Open Orange.
Select New to create a blank workflow.
In the widget search box, type:
Datasets
Drag the Datasets widget onto the canvas.
Double-click the widget.
Search for:
Telecom
Select the available telecom customer-churn dataset.
Allow the dataset to load.
Orange’s official business example confirms that telecom customer-churn data can be loaded through the Datasets widget. Orange customer-segmentation example
If the Telecom Dataset Is Not Visible
Search for:
Churn
Select the available customer-churn dataset.
If neither search produces a result, use the dataset file supplied by the faculty.
Drag the File widget onto the canvas.
Double-click File.
Browse to the supplied .csv file.
Select Open.

Inspect the Dataset
Add a Data Table
Search for the Data Table widget.
Drag it onto the canvas.
Connect:
Datasets → Data Table
Double-click Data Table.
Observe:
Number of rows
Number of columns
Column names
Feature values
Target variable
Record the Following
Create a document named:
dataset-understanding.md
Complete:
Dataset name:

Business problem:

One row represents:

Number of rows:

Number of columns:

Target variable:

Possible numerical features:

Possible categorical features:

Possible identifier columns:

Inspect Data Quality
Add Feature Statistics
Search for Feature Statistics.
Drag it onto the canvas.
Connect:
Datasets → Feature Statistics
Open the widget.
Examine:
Variable types
Missing values
Minimum and maximum values
Value distribution
Unusual categories
Add Distributions
Search for Distributions.
Place it on the canvas.
Connect:
Datasets → Distributions
Open the widget.
Select different variables.
Use the target variable as the colour or grouping variable if available.
Observe whether churn patterns appear different across customer groups.
Record at Least Three Observations
Examples:
A particular contract group appears to have more churn.
Customers with a particular usage pattern appear more likely to leave.
Some variables contain missing values.
One class has more records than the other.
Do not report a pattern unless it is visible in the data.

Select Features and Target
Add Select Columns
Search for Select Columns.
Drag it onto the canvas.
Connect:
Datasets → Select Columns
Open Select Columns.
Review the available variables.
Orange normally separates variables into:
Features
Target
Meta attributes
Skipped variables
Configure the Variables
Keep business-relevant inputs under Features.
Keep the churn outcome under Target.
Move customer ID or reference number to Meta Attributes.
Move clearly irrelevant columns to Skipped Variables.
Why Move Customer ID?
Customer ID identifies a customer, but the number itself normally does not explain why the customer may churn.

Create the Preprocessing Pipeline
Add Preprocess
Search for Preprocess.
Drag it onto the canvas.
Connect:
Select Columns → Preprocess
Double-click Preprocess.
Add suitable preprocessing steps.
Depending on the dataset, select:
Impute for missing values
Continuize for converting categories into model-usable numerical representations
Normalize where scaling is useful
Important Modelling Practice
For evaluation, connect the Preprocess widget to Test and Score, not directly to a separate final data output used before cross-validation.
Orange’s current documentation warns that preprocessing the complete dataset before cross-validation can cause data leakage and overfitting. The recommended workflow is to connect the preprocessor to Test and Score, so preprocessing is applied within each evaluation fold. Orange Test and Score documentation

Add Classification Algorithms
Add these three widgets from the Model category:
Logistic Regression
Tree
Random Forest
Place them on the canvas.
At this stage, keep the default settings.
Conceptual Meaning
Logistic Regression: Estimates the probability of churn.
Tree: Creates decision-like rules.
Random Forest: Combines multiple Decision Trees.

Add Test and Score
Search for Test and Score.
Drag it onto the canvas.
Create these connections:
Select Columns → Test and Score
Preprocess → Test and Score
Logistic Regression → Test and Score
Tree → Test and Score
Random Forest → Test and Score
Open Test and Score.
Select Cross-validation.
Use the default number of folds unless instructed otherwise.
Select Stratified if it is available and the target classes are imbalanced.
Orange’s Test and Score widget supports cross-validation and displays classification performance measures for comparing multiple learners. Test and Score

Read the Model Results
The results may show columns such as:
AUC
CA
F1
Precision
Recall
In Orange:
CA means Classification Accuracy.
Higher scores are generally better.
A high value does not automatically make a model suitable for every business situation.
Complete this table using the actual results displayed:
Model
Accuracy/CA
Precision
Recall
F1-Score
Logistic Regression








Decision Tree








Random Forest









Take a screenshot and save it as:
model-comparison.png

View the Confusion Matrix
Search for Confusion Matrix.
Drag it onto the canvas.
Connect:
Test and Score → Confusion Matrix
Open Confusion Matrix.
Select one model at a time.
Compare correct and incorrect predictions.
Observe how many churned customers were missed.
Observe how many non-churned customers were incorrectly flagged.
Save a screenshot as:
confusion-matrix.png

Interpret the Errors
For customer churn:
False Positive
The model predicts that a customer will leave, but the customer would actually stay.
Possible Business Cost
Unnecessary discount
Unnecessary customer contact
Wasted retention budget
False Negative
The model predicts that a customer will stay, but the customer actually leaves.
Possible Business Cost
Lost customer
Lost future revenue
Missed retention opportunity
Business Question
For this company, is it more costly to contact some customers unnecessarily or to miss customers who are genuinely likely to leave?
There is no universal answer. The decision depends on:
Cost of the retention offer
Value of the customer
Expected loss from churn
Available marketing budget

Save the Orange Workflow
Select File.
Select Save As.
Open the workflow folder.
Save the file as:
telecom-churn-model.ows
The .ows file preserves the complete Orange workflow.
The final workflow should contain:
Datasets
├── Data Table
├── Feature Statistics
├── Distributions
└── Select Columns
    └── Test and Score
        └── Confusion Matrix

Preprocess ───────────→ Test and Score
Logistic Regression ─→ Test and Score
Tree ────────────────→ Test and Score
Random Forest ───────→ Test and Score

Prepare the Model Evaluation Report
Create a Google Doc titled:
Telecom Customer Churn: No-Code ML Report
Use the following structure.
Business Problem
A telecom company wants to identify customers who may discontinue its services. Early identification can help the company prioritize suitable retention actions.
Type of Machine Learning
This is a supervised classification problem because the target variable represents categories such as churn and no churn.
Dataset
Write:
What one row represents
Number of rows and columns
Target variable
Important features
Data-quality observations
Preprocessing
Explain:
Whether missing values were present
Which variables were selected
Which identifier or irrelevant columns were removed
Which preprocessing steps were applied
Why preprocessing was required
Models Compared
Logistic Regression
Decision Tree
Random Forest
Evaluation Results
Paste the completed model comparison table.
Confusion Matrix Interpretation
Explain:
Correct churn predictions
Correct non-churn predictions
False positives
False negatives
Which type of error may be more costly
Recommended Model
Use this format:
The recommended model is __________.

It achieved __________ Accuracy, __________ Precision, __________ Recall and an F1-score of __________.

This model is recommended because ________________________________.

However, the company should also consider ________________________.
Business Actions
The company may:
Prioritize high-risk customers.
Investigate common causes of churn.
Provide suitable retention support.
Improve service for high-risk customer groups.
Monitor whether retention actions are effective.
Limitations
Include:
The model may make incorrect predictions.
Historical data may contain bias.
Customer behaviour can change.
Model performance may reduce on future data.
A prediction does not prove why a customer will leave.
Real customer data requires privacy protection.
Business impact must be monitored after deployment.
Human Oversight
The model should identify risk, but a manager should review customer history, fairness, customer value and the cost of the proposed action before approving a retention offer.
Download the document as:
telecom-churn-ml-report.pdf

GitHub Portfolio Documentation
Add this project to the existing repository:
bba-ai-ml-portfolio
Create the following file:
part-a/supervised-learning/README.md
GitHub README Template
# Telecom Customer Churn Prediction Using No-Code Machine Learning

## Project Overview

This project uses Orange Data Mining to build and compare supervised classification models for telecom customer churn prediction. The complete workflow was created without programming.

## Business Problem

A telecom company wants to identify customers who may discontinue its services so that managers can prioritize appropriate retention actions.

## Machine Learning Task

This is a supervised classification problem.

## Target Variable

The target variable represents whether a customer churned.

## Key Features

[List the important features present in the selected dataset.]

## Data Preparation

The dataset was inspected for variable types, missing values, irrelevant columns and possible data-quality problems. Customer identifiers were not used as predictive features.

## Models Evaluated

- Logistic Regression
- Decision Tree
- Random Forest

## Evaluation Metrics

The models were compared using:

- Classification Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

## Results

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| Logistic Regression | [Enter] | [Enter] | [Enter] | [Enter] |
| Decision Tree | [Enter] | [Enter] | [Enter] | [Enter] |
| Random Forest | [Enter] | [Enter] | [Enter] | [Enter] |

## Recommended Model

[Name the selected model and explain why it was selected.]

## Business Interpretation

False positives may cause unnecessary retention spending. False negatives may result in the company missing customers who are genuinely likely to leave. The preferred balance depends on customer value, retention cost and business priorities.

## Business Recommendations

- Prioritize customers with a higher predicted churn risk.
- Investigate complaints and service issues.
- Provide suitable rather than automatic discounts.
- Measure the success of retention actions.
- Keep a manager involved in final customer decisions.

## Limitations

- Predictions may be incorrect.
- Historical data may contain bias.
- Model performance may change over time.
- Prediction does not establish causation.
- Real customer data requires privacy protection.

## Tools Used

- Orange Data Mining
- Google Docs
- GitHub

## Project Files

- Orange workflow
- Model comparison screenshot
- Confusion Matrix screenshot
- Model evaluation report

## Skills Demonstrated

- Data-quality assessment
- Data preprocessing
- Feature selection
- Supervised Machine Learning
- Classification modelling
- Model comparison
- Confusion Matrix interpretation
- Business-focused model evaluation
- No-code Machine Learning
- GitHub project documentation

## AI Usage Declaration

This project was completed using a no-code visual Machine Learning tool. The reported performance values were obtained from the Orange workflow and were not invented or manually modified.

Upload the Project Files
Upload:
part-a/supervised-learning/
├── README.md
├── telecom-churn-model.ows
├── telecom-churn-ml-report.pdf
├── dataset-understanding.md
├── model-comparison.png
└── confusion-matrix.png
Use the commit message:
Add no-code telecom churn classification project

Submission Checklist
Orange Data Mining is installed and working.
The customer-churn dataset is loaded.
The dataset is connected to Data Table.
Variable types and distributions are inspected.
The target variable is correctly assigned.
Identifier columns are not used as predictive features.
Preprocess is connected correctly to Test and Score.
Logistic Regression is included.
Decision Tree is included.
Random Forest is included.
Cross-validation is used.
Accuracy, Precision, Recall and F1-score are recorded.
The Confusion Matrix is interpreted.
False positives and false negatives are explained.
A model is recommended using business reasoning.
The Orange .ows workflow is saved.
The project report is complete.
The GitHub README is complete.
All files are uploaded to the correct folder.
The GitHub link opens correctly.

Knowledge Check
Why is data preprocessing required?
What is the difference between feature selection and feature engineering?
What is supervised learning?
How is classification different from regression?
What is the purpose of training data?
What is the purpose of testing data?
Why should Customer ID not normally be used as a predictive feature?
What does Accuracy measure?
What does Precision measure?
What does Recall measure?
When is F1-score useful?
What does a False Negative mean in customer churn?
Why should a business manager examine more than Accuracy?
Why must human oversight remain part of the workflow?

Skills Developed
Data-quality assessment
Data preprocessing
Feature selection
Feature-engineering concepts
Supervised Machine Learning
Classification and regression concepts
Logistic Regression
Decision Tree
Random Forest
Accuracy, Precision, Recall and F1-score
Confusion Matrix interpretation
No-code Machine Learning with Orange
Business-focused model evaluation
GitHub portfolio documentation
Portfolio Evidence Statement
Built and evaluated a no-code customer-churn classification workflow in Orange Data Mining; prepared business data, compared Logistic Regression, Decision Tree and Random Forest using Accuracy, Precision, Recall and F1-score, and interpreted classification errors through a Confusion Matrix.
Resume Bullet After Completing the Course
Built and evaluated a no-code telecom customer-churn classification workflow using Orange Data Mining; applied preprocessing and feature selection, compared Logistic Regression, Decision Tree and Random Forest, interpreted Accuracy, Precision, Recall, F1-score and Confusion Matrix, and documented results in a GitHub portfolio.

