# Data-Science-Job-Recommendation-System
A job recommendation and salary prediction system based on content-based filtering to recommend data science jobs along with the predicted salary by resume parsing.
 
 ### Motivation
The motivation to do this project was to help a student understand what should be the right job for him/her based on one's skills, experience and education and the salary that one is worth based on these parameters. Many students strive to secure Data Scientist jobs upon completion of educational programs. They often wonder what tools are needed, what opportunities and job titles are available, and the salaries associated with the roles. Understanding what would be best for students to pursue is important in their job search.
 
 ### Problem Statement
Given a resume, recommend jobs from a given dataset of various companies comprising of the job descriptions and their profile and predict salary for the student
 
 ### Dataset
This datas is scraped from the Glassdoor website using Selenium scrapper. After scraping, the raw dataset was cleaned and made usable for performing data analysis and modelling. The dataset contains information about the minimum salary, maximum salary, average salary, job description, age of the company in years, etc.
 
 ### Technical Details
 
 #### Libraries
 * pandas & numpy - for data wrangling and mathematical operations
 * nltk - for information retrieval from job descriptions
 * sklearn - for feature engineering, model building and model evaluation
 * requests & json - for using stackoverflow api as the database for the skillsets required
 * pyresparser & pypdf2 - for extracting relevant information from resume 
 * bayes_opt - for hyperparameter tuning using Bayesian Optimization

#### Feature Engineering
 
