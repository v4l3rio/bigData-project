# Big Data Project – Sentiment Analysis and Frequent Pattern Mining

## Overview

This project analyzes Amazon book reviews using Apache Spark to perform two main tasks:

1. **Sentiment Analysis using Word Lists**
2. **Frequent Pattern Mining using FPGrowth**

The goal is to process a large dataset of Amazon book reviews and extract meaningful insights by combining classical text‐processing techniques with distributed data processing.

---

## Technologies Used

* **Apache Spark (RDD, DataFrame, Dataset APIs)**
* **Spark MLlib (Tokenizer, StopWordsRemover, FPGrowth)**
* **Scala**
* **Amazon S3 (for dataset storage)**

---

## Project Objectives

* Evaluate the sentiment of Amazon book reviews using predefined lists of positive and negative words.
* Estimate a rating score consistent with Amazon’s 1–5 star system through statistical normalization.
* Identify frequent word patterns within reviews using association rule mining.
* Handle large‐scale data processing efficiently using distributed systems and optimization techniques such as caching and broadcast variables.

---

## Solution Approach

### 1. Sentiment Analysis (Job 1)

The sentiment analysis is based on a lexicon approach using positive and negative word lists. The process includes:

* Cleaning and tokenizing review text.
* Counting occurrences of positive and negative words using broadcast variables for efficiency.
* Computing a sentiment weight per review as the difference between positive and negative occurrences.
* Filtering out outliers based on manually selected thresholds to improve normalization.
* Applying Z-score normalization followed by Min-Max scaling to convert sentiment weight into an estimated Amazon-style rating from 1 to 5.
* Computing the relative error between predicted and real ratings to evaluate performance.

### 2. Frequent Pattern Mining (Job 2)

This step extracts recurrent groups of words from the reviews:

* Cleaning and preparing text through tokenization and stopword removal.
* Ensuring uniqueness of words within each review as required by FPGrowth.
* Removing trivial or overly frequent words using a blacklist to highlight more meaningful patterns.
* Using **Spark MLlib’s FPGrowth** to compute frequent itemsets with given support and confidence thresholds.
* Analyzing the most frequent patterns found across all reviews.

