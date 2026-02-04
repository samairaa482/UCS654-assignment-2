
# NO₂ Data Transformation and PDF Parameter Estimation

## Problem Overview
This project performs a mathematical transformation on **NO₂ air quality data** and then learns the parameters of a specified probability density function (PDF).  
The task is divided into three main steps as required by the assignment.

## Dataset
- **Source:** Kaggle – India Air Quality Data  
- **Feature Used:** `NO2`  
- Missing values are removed before processing.


## Constant


Using the formulas:

- \( a_r = 0.05 \times (r \bmod 7) \)
- \( b_r = 0.3 \times (r \bmod 5 + 1) \)

We get:

- **a_r = 0.05**
- **b_r = 1.5**


## Step 1: Data Transformation

The NO₂ values (x) are transformed into a new variable (z) using:

\[
z = x + a_r \sin(b_r x)
\]

Substituting constants:

\[
z = x + 0.05 \sin(1.5x)
\]

### Intuition
- Adds a small non-linear perturbation
- Simulates real-world environmental fluctuations
- Preserves the original data trend

## tep 2: Probability Density Function Learning

Target PDF:

\[
\hat{p}(z) = c \cdot e^{-\lambda (z - \mu)^2}
\]

This is equivalent to a **Gaussian distribution**.

### Parameter Estimation Method
**Maximum Likelihood Estimation (MLE)** is used:

- **mu (mean)** → sample mean of z
- **sigma² (variance)** → sample variance of z
- **lambda = 1 / (2sigma²)**
- **c = √(lambda / pi)**

This method is:
- Statistically optimal
- Closed-form


## Visualization
- Histogram of transformed data (z)
- Overlay of learned PDF curve
- Confirms goodness of fit


## How to Run

1. Download the dataset from Kaggle
2. Place the CSV file in the project folder
3. Run the Python script in one go
4. Copy the printed values of lambda, mu, and c for submission


## Libraries Used
- Python 3
- NumPy
- Pandas
- Matplotlib


