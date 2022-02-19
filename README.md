# Data-Science-Job-Recommendation-System
A job recommendation and salary prediction system based on content-based filtering to recommend data science jobs along with the predicted salary by resume parsing.
 
 ### Motivation
The motivation to do this project was to help a student understand what should be the right job for him/her based on one's skills, experience and education and the salary that one is worth based on these parameters. Many students strive to secure Data Scientist jobs upon completion of educational programs. They often wonder what tools are needed, what opportunities and job titles are available, and the salaries associated with the roles. Understanding what would be best for students to pursue is important in their job search.
 
 ### Problem Statement
Given a resume, recommend jobs from a given dataset of various companies comprising of the job descriptions and their profile and predict salary for the student
 
 ### Dataset
This data is scraped from the Glassdoor website using Selenium scrapper. After scraping, the raw dataset was cleaned and made usable for performing data analysis and modelling. The dataset contains information about the minimum salary, maximum salary, average salary, job description, age of the company in years, etc.<br>
An additional dataset is used to incorporate cost of living for US cities while predicting salary.
 
 ### Technical Details
 
 #### Libraries
 * pandas & numpy - for data wrangling and mathematical operations
 * nltk and re - for information retrieval from job descriptions
 * sklearn - for feature engineering, model building and model evaluation
 * requests & json - for using stackoverflow api as the database for the skillsets required
 * pyresparser & pypdf2 - for extracting relevant information from resume 
 * bayes_opt - for hyperparameter tuning using Bayesian Optimization

#### Feature Engineering
* Recommendation
  * binning job titles into data engineer, ml engineer, data scientist and data analyst
  * creating a DB for skills from stackoverflow and looking for those keywords in job description using unigram and bigram tokenization to list all the skills for that job
  * extracting years of experience from job description using regex and job title
  * binning industries from sectors
  * dummy encoding degree, previous job titles, industries worked and skillset
* Salary
  * binning company size
  * taking median salary as the response variable since salary tends to be right skewed
  * imputing mean state cost of living for cities missing
  * using Non-Matrix Factorization for dimensionality reduction of skills
* Resume
  * mapping degree, previous job titles, experience, industries worked and skillset using unigram and bigram tokenization from resume parsing
  * dummy encoding them to match the features with features of the original data

#### Modeling
* Recommendation
  * filtering the jobs from original data on the experience calculated from resume
  * defining a cosine similarity function and mapping degree, previous job titles, industries worked and skillset individually using the function
  * scaling the similarity for standardization to prevent undue advantage of any feature
  * multiplying the scaled features with a weightage matrix of degree, previous job titles, industries worked and fetching top 3 highest values for unique companies
* Salary
  * using bayesian optimization for hyperparameter tuning while training XGBoost
  * getting the company features and location (cost of living) from the recommendations and manipulating them to match the training data
  * transforming skills based on fitted Non-Matrix Factorization
  * predicting salary for each of the 3 recommendations

#### Evaluation
* Recommendation
  * TODO: Missing validating dataset to check how good the recommendation is
* Salary
  * Mean absolute error of $11k salary before hyperparameter tuning and $9k salary after on cross-validation 

#### Result
An array of json objects containing company, job title, location and salary 
 
