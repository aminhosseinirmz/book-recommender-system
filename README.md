# Book Recommender System

A book recommendation system built with Apache Spark using multiple recommendation approaches on a large-scale book ratings dataset.

## Overview

This project explores different strategies for recommending books by combining data preprocessing, exploratory analysis, and several recommendation algorithms.

The system includes:

- Popularity-based recommendation
- Collaborative filtering with ALS
- Item-based collaborative filtering
- Content-based filtering using TF-IDF and CountVectorizer
- Hybrid recommendation approaches

## Dataset

The project uses a dataset containing three CSV files for:

- Users
- Books
- Ratings

The dataset includes hundreds of thousands of users, books, and ratings, making it suitable for large-scale recommender system experiments.

## Methods

### 1. Data Cleaning
The raw books, users, and ratings tables are cleaned and prepared for analysis.

### 2. Exploratory Data Analysis
The notebook includes visual analysis of features such as:

- Year of publication
- Rating distribution
- User age

### 3. Popularity-Based Recommendation
Several popularity-driven recommenders are implemented, including:

- Top books overall
- Top books by location
- Top books by author or publisher
- Year-based recommendation
- Weighted average rating

### 4. Collaborative Filtering
Collaborative recommendation methods include:

- ALS (Alternating Least Squares) using Spark MLlib
- Item-based collaborative filtering

### 5. Content-Based Filtering
Content-based methods are built using text representations such as:

- TF-IDF
- CountVectorizer

### 6. Hybrid Recommendation
The project also explores combining models through:

- Switched ensemble
- Weighted ensemble

## Technologies Used

- Python
- Apache Spark / PySpark
- Pandas
- NumPy
- Matplotlib
- Scikit-learn

## Files

- `book-recommender-system.ipynb` — main notebook containing the full workflow
- `Book Recommendation.pptx` — presentation slides for the project

## How to Run

1. Install the required Python libraries
2. Start a local Spark session
3. Open the notebook
4. Update the dataset paths if needed
5. Run the cells in order

## Notes

This project was developed as an academic recommender systems / big data project focused on comparing multiple recommendation strategies on book data.
