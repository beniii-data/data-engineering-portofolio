# Data Cleaning & Reconstruction Project

# Overview
This project focuses on cleaning, standardizing, and reconstructing a transactional dataset consisting of ~10,001 rows and 8 columns.

The raw dataset contained inconsistent formatting, disorganized column structures, and missing values across several key fields. The goal of this project was to transform the dataset into a clean, structured, and analysis-ready format using rule-based data cleaning and logical reconstruction techniques.

---

## Dataset Structure

The cleaned dataset contains the following columns:

  * transaction_id
  * item
  * quantity
  * price_per_item
  * total_spent
  * payment_method
  * location
  * transaction_date

---

## Data Cleaning Process

	1. Column Standardization
      The original dataset had messy and inconsistent column formatting. The following steps were applied:

		* Reorganized columns using Excel shortcuts:
		
		  * `Alt + H + O + A` (AutoFit Column Width)
		  * `Alt + H + O + I` (AutoFit Row Height)
		  * Trimmed unnecessary spaces
		  * Converted all column headers to lowercase
		  * Replaced spaces with underscores (`_`) for consistency

---

	2. Handling Missing Values

		# Numerical Reconstruction

			Missing values in numerical columns were reconstructed using mathematical relationships:
			
			* `total_spent = price_per_item × quantity`
			
			Reconstruction logic:
			
			* Missing `price_per_item` → calculated using `total_spent / quantity`
			* Missing `quantity` → calculated using `total_spent / price_per_item`

---

		# Item-Based Imputation

			* Identified that identical items tend to have consistent pricing
			* Missing `price_per_item` values were filled using known prices from the same item in other rows

---

# Unrecoverable Cases
Some data could not be reconstructed due to insufficient information:

	* Rows where both `quantity` and `total_spent` were missing
	* Cases where multiple items shared identical prices, making reverse identification unreliable
	
	These values were left as missing to preserve data integrity.

---

# Key Insights

	* Mathematical relationships are effective for recovering missing numerical values
	* Item-based imputation works well but depends on data consistency
	* Price alone is not a unique identifier for items
	* Some level of data loss is unavoidable in incomplete datasets

---

# Output

	* Cleaned and standardized dataset
	* Reconstructed missing values where logically possible
	* Remaining missing values clearly identified

---

# Future Improvements

	* Implement automated cleaning using Python (Pandas)
	* Apply advanced imputation techniques (e.g., statistical or ML-based)
	* Add validation checks to detect anomalies after reconstruction

---

#Author Notes
This project emphasizes practical problem-solving in real-world messy data scenarios.
All cleaning and reconstruction steps were performed using rule-based logic and manual validation to ensure consistency and reliability.

---

# Tools Used

* Microsoft Excel

---

# Closing

This project demonstrates the ability to handle raw, unstructured data and transform it into a reliable dataset ready for analysis.