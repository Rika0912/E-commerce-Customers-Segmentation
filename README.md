# E-commerce-Customers-Segmentation Using Unsupervised Learning


## Overview

This project applies **unsupervised machine learning** techniques to perform **customer segmentation** based on transactional behavior and demographic information from a dataset. The segmentation aims to identify distinct groups of customers that exhibit similar behaviors, enabling business stakeholders to make informed decisions about targeted marketing strategies, coupon offers, and customer loyalty programs.

The dataset is stored in an Excel file, containing six different tables: `Customers`, `Genders`, `Cities`, `Transactions`, `Branches`, and `Merchants`. By analyzing these tables, we derive insights into customer behaviors such as transaction frequency, coupon burn rate, and demographic information (gender, city). We then use these features to perform customer segmentation via **K-Means clustering**.

## Project Workflow

### 1. **Data Loading**
The data is read from an Excel file (`E-commerce_data.xlsx`) using the `pandas` library. Each table in the Excel file corresponds to a different sheet:
- **Customers**: Contains customer demographics like city and gender.
- **Genders**: Lists the available genders.
- **Cities**: Contains city identifiers.
- **Transactions**: Includes details of customer coupon transactions.
- **Branches**: Represents the branches where the coupons were burnt.
- **Merchants**: Provides merchant information.

### 2. **Data Merging**
The tables are merged to create a single dataset containing customer information, transaction history, gender, and city. Key steps include:
- Merging **customers** with **transactions**, **genders**, and **cities** using customer, gender, and city identifiers.

### 3. **Feature Engineering**
We engineer several key features that are crucial for customer segmentation:
- **Transaction Frequency**: The total number of transactions each customer has performed.
- **Burn Rate**: The proportion of coupons claimed by the customer that were actually burnt (used).
- **Demographic Data**: Customer gender and city are included to provide demographic context for the clustering process.

### 4. **Data Preprocessing**
To prepare the data for clustering, the relevant features are standardized using `StandardScaler`. This ensures that all features are on the same scale, which is critical for effective clustering.

### 5. **K-Means Clustering**
We perform clustering using the **K-Means** algorithm to group customers into distinct segments. Key steps include:
- **Exploring Cluster Numbers**: We experiment with different values for the number of clusters (K), ranging from 2 to 10. For each value of K, we compute:
  - **Silhouette Score**: Measures how similar a data point is to its own cluster compared to other clusters.
  - **Inertia**: The sum of squared distances between data points and the center of their assigned clusters.
  
  We use the **elbow method** and the silhouette score to determine the optimal number of clusters.

### 6. **Model Evaluation**
We select the optimal number of clusters (in this case, K=4) based on the evaluation metrics:
- **Silhouette Score**: Helps identify well-separated clusters.
- **Inertia**: Assesses how compact the clusters are.

### 7. **Segment Analysis**
For each cluster, we analyze key features such as:
- **Transaction Frequency**: How often customers from this segment make transactions.
- **Burn Rate**: The likelihood that customers from this segment use (burn) the coupons they claim.
- **Demographics**: The gender and city distribution within each segment.

### 8. **Recommendations**
Based on the analysis of each segment, we recommend targeted marketing strategies:
- **High Transaction Frequency & High Burn Rate**: Offer loyalty rewards to these customers, as they are highly engaged and likely to use coupons.
- **Moderate Burn Rate**: Provide targeted discounts to increase coupon usage.
- **Low Engagement**: Engage these customers with personalized offers to increase their activity.

### 9. **Visualization**
We visualize the results using `matplotlib` and `seaborn`:
- **Silhouette Score Plot**: Displays the silhouette scores for different cluster values (K) to help determine the optimal number of clusters.
- **Inertia Plot**: Shows the sum of squared distances for each cluster number, helping to identify the "elbow point."
- **Cluster Scatter Plot**: Visualizes the customer segments based on their transaction frequency and burn rate.

## Key Insights
1. **Customer Segments**: We identified four distinct customer segments based on transactional behavior and demographics.
2. **Loyalty Indicators**: Customers with higher transaction frequencies and burn rates are more likely to remain loyal and should be rewarded with high-value coupons.
3. **Targeted Marketing**: Different customer segments require different marketing approaches, from offering loyalty rewards to re-engaging less active customers.

## How to Run the Project

### Prerequisites
Ensure the following Python libraries are installed:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

### Steps to Run the Code
1. Place the Excel file (`E-commerce_data.xlsx`) containing the six tables in the same directory as the script.
2. Adjust the `file_path` variable in the script to match the location of your Excel file.
3. Run the Python script. The program will load the data, perform clustering, and output visualizations along with recommendations for each customer segment.

## Conclusion

This project provides a comprehensive solution for segmenting customers based on their demographic and transactional data. By using unsupervised machine learning, we can better understand customer behavior and create data-driven strategies to enhance customer loyalty and satisfaction. The visualizations and recommendations offer actionable insights for businesses looking to personalize their marketing efforts.
