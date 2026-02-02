# Probability-Density-Functions-using-Roll-Number-Parameterized-Non-Linear-Model

## Project Overview

This project performs statistical modeling and probability density estimation on atmospheric NO₂ (Nitrogen Dioxide) concentration data.  
A roll-number–parameterized nonlinear transformation is applied to the data, and the resulting distribution is modeled using a Gaussian-type probability density function (PDF).

The objective is to estimate distribution parameters and validate the fitted model by comparing it with the histogram of the transformed samples.

---

## 1. Methodology

### 1.1 Data Preprocessing

- Loaded NO₂ concentration data from a CSV file  
- Removed invalid and missing values  
- Converted all values to numeric format  
- Extracted NO₂ values into a NumPy array  

---

### 1.2 Nonlinear Data Transformation

Each NO₂ value `x` is transformed using the nonlinear function:

z = x + α sin(βx)

Where:

α = 0.05 × (roll_number mod 7)  
β = 0.3 × ((roll_number mod 5) + 1)

This transformation introduces controlled oscillations into the data.

---

### 1.3 Histogram-Based Density Estimation

- A normalized histogram of the transformed variable `z` is computed  
- Midpoints of histogram bins are calculated  
- These midpoints serve as empirical density values  

---

### 1.4 Probability Density Function

The Gaussian-type PDF used is:

f(z) = c · exp(−λ (z − μ)²)

Where:

λ controls the spread  
μ is the mean  
c = √(λ / π)

---

### 1.5 Parameter Estimation

- Initial estimates are computed using sample mean and variance  
- `curve_fit` is used to estimate λ and μ  
- The normalization constant `c` is calculated from λ  

---

## 2. Input

- Dataset: `data.csv`  
- Feature: `NO2` (Nitrogen Dioxide concentration)  



## 3. Output

- Estimated parameters: λ, μ, c  
- Histogram of transformed samples  
- Fitted probability density curve  
- Visual comparison between data and model  


## 4. Key Results

- The nonlinear transformation produces a right-skewed distribution  
- The fitted PDF closely matches the histogram  
- The model accurately captures the mean and variance of the data  


## 5. Conclusion

This project demonstrates how nonlinear transformations and probability density estimation can be combined to model environmental pollution data.  
The fitted distribution provides a compact statistical summary of NO₂ concentration behavior after transformation, making it useful for analysis and prediction.
