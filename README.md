# Book Recommender System with Apache Spark

A large-scale book recommendation project built with **Apache Spark / PySpark** on the **Book-Crossing (BX)** dataset.

This project explores how different recommendation strategies behave on real user-book interactions. It covers the full workflow from **data loading and cleaning** to **visual analysis**, **multiple recommendation approaches**, and **hybrid recommenders**.

The notebook implements and compares:

- popularity-based recommendation
- weighted average ranking
- collaborative filtering with **ALS**
- item-based collaborative filtering using similarity functions
- content-based recommendation using **TF-IDF** and **CountVectorizer**
- hybrid recommendation with **switched** and **weighted ensemble** methods

The dataset used in this project contains **278,858 users**, **1,149,780 ratings**, and **271,379 books**.

---

## Project Overview

In large online catalogs, users are often overwhelmed by the number of available items. Recommender systems help solve this by ranking items that are likely to be useful, relevant, or interesting for a user.

This project focuses on **book recommendation at scale** using **Apache Spark**, which makes it possible to process large datasets efficiently in a distributed way. The notebook shows both the **data engineering side** and the **recommendation side** of the problem.

The work is organized into these main stages:

1. environment setup and Spark session creation
2. loading books, users, and ratings data
3. cleaning invalid, missing, and duplicated values
4. exploratory data analysis and visualization
5. building several recommender systems
6. basic evaluation and comparison of methods

---

## Dataset

The project uses the **Book-Crossing dataset**, composed of three CSV files:

- `BX-Books.csv`
- `BX-Users.csv`
- `BX-Book-Ratings.csv`

These files represent:

- **books metadata**
- **user information**
- **user-book ratings**

The notebook works with both **implicit and explicit ratings**, but the main personalized recommendation models are built on the **explicit ratings subset**. :contentReference[oaicite:3]{index=3}

---

## Features Implemented

### 1. Data Cleaning

The notebook performs cleaning on all three dataframes:

#### Books
- removes unused image URL columns
- fixes invalid and misplaced values
- corrects malformed publication year entries
- replaces missing author/publisher values
- converts publication year to integer
- standardizes ISBN format
- removes duplicate rows

#### Users
- cleans invalid and missing age values
- replaces unrealistic ages with a reasonable estimate
- converts age to integer
- splits location into:
  - city
  - state
  - country
- normalizes text values
- handles missing location parts

#### Ratings
- standardizes ISBN format
- checks validity of ratings
- removes duplicates

---

### 2. Data Visualization

The notebook includes exploratory plots to better understand the dataset, such as:

- publication year distribution
- rating distribution
- explicit vs implicit ratings
- user age distribution

This helps reveal important patterns before building recommenders, including the fact that a large portion of ratings are implicit.

---

### 3. Recommendation Systems

The main part of the project implements several recommendation strategies.

#### A. Popularity-Based Recommenders

Non-personalized recommendation methods including:

- top books in the whole collection
- top books by location
  - city
  - state
  - country
- top books by the same author
- top books by the same publisher
- top books by publication year
- weighted average ranking

These methods are simple, fast, and useful as strong baselines.

---

#### B. Collaborative Filtering — ALS

The project implements **Alternating Least Squares (ALS)** using Spark MLlib.

Main steps:
- filter low-support books to reduce sparsity
- convert user and item identifiers into numeric form
- split data into training and test sets
- train ALS model
- evaluate predictions with **RMSE**
- generate top-N recommendations for users

This is the matrix-factorization part of the project and serves as the main model-based collaborative filtering approach.

---

#### C. Collaborative Filtering — Item-Based Similarity

The notebook also implements item-based collaborative filtering using similarity functions.

Implemented similarity methods:
- cosine similarity
- Pearson similarity
- adjusted cosine similarity

These methods are used to:
- recommend similar books for a given book
- recommend books for a given user based on previously rated items

This part is useful because it is more interpretable than matrix factorization and makes book-to-book recommendations easier to explain.

---

#### D. Content-Based Recommendation

The project builds content-based recommenders from book metadata using text features.

Implemented methods:
- **TF-IDF**
- **CountVectorizer**

These are used to create:
- book-to-book recommendations
- user-based recommendations derived from content similarity

This is helpful especially when collaborative signals are weak or when item metadata carries meaningful information.

---

#### E. Hybrid Recommenders

Two hybrid strategies are included:

- **Switched ensemble recommender**
- **Weighted ensemble recommender**

These combine the strengths of multiple recommenders instead of relying on only one method.

Hybrid systems are useful because:
- popularity works well for cold-start and broad appeal
- collaborative filtering captures user behavior
- content-based filtering works when metadata is informative

Combining them often produces more robust recommendations. :contentReference[oaicite:4]{index=4}

---

## Tech Stack

- **Python**
- **Apache Spark / PySpark**
- **Spark SQL**
- **Spark MLlib**
- **NumPy**
- **Matplotlib**
- **PySpark ML Feature Transformers**
  - `Tokenizer`
  - `HashingTF`
  - `IDF`
  - `CountVectorizer`

---

## Notebook Structure

The notebook is organized as follows:

- **0. Setting up development environment**
- **1. Setting up Apache Spark**
- **2. Loading data**
- **3. Data Cleaning**
- **4. Data Visualization**
- **5. Recommendation Systems**
  - popularity-based
  - weighted average
  - ALS collaborative filtering
  - item-based collaborative filtering
  - content-based filtering
  - hybrid recommenders

This makes the notebook easy to follow from raw data to final recommendations.

---

## Example Recommendation Tasks Covered

The notebook supports use cases such as:

- recommend the most popular books overall
- recommend top books in a specific country, state, or city
- recommend books by the same author or publisher
- recommend books similar to a given book
- recommend books for a specific user
- compare collaborative and content-based methods
- combine multiple recommenders in a hybrid system

---

## Evaluation

The notebook includes model evaluation for ALS using **RMSE** and also discusses recommendation quality concepts such as:

- diversity
- coverage
- serendipity
- feedback loops

These are important because a recommender should not only be accurate, but also useful and varied. :contentReference[oaicite:5]{index=5}

---

## How to Run

1. Install dependencies
2. Make sure the dataset files are available in the expected `data/` directory
3. Launch Jupyter Notebook or Google Colab
4. Open:

```bash
book-recommender-system. final.ipynb
