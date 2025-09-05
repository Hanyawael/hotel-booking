# hotel-booking
# Hotel Booking Data Preprocessing Project

## 📌 Project Overview
This project is part of the **GTC ML Project 1** challenge.  
The goal is to build a **robust data preprocessing pipeline** for a hotel booking cancellation prediction model.  
We focus only on preparing the dataset, not training the final ML model.

### 🏨 Business Problem
Last-minute booking cancellations significantly impact hotel profitability.  
A high-quality, cleaned dataset is required for predictive modeling to help the revenue team reduce losses.

---

## ⚙️ Project Phases

### Phase 1: Exploratory Data Analysis (EDA)
- Loaded dataset and generated `.info()` and `.describe()`.
- Identified missing values and visualized them using `missingno`/heatmap.
- Detected outliers in key features (`adr`, `lead_time`) using boxplots and IQR.

### Phase 2: Data Cleaning
- **Missing Values**  
  - `company`, `agent` → replaced with "None"/0  
  - `country` → imputed with mode or "Unknown"  
  - `children` → imputed with median/mode  
- **Duplicates** → removed exact duplicates  
- **Outliers** → capped extreme ADR values (e.g., >1000 set to 1000)  
- **Data Types** → fixed date formats  

### Phase 3: Feature Engineering & Preprocessing
- Created new features:
  - `total_guests = adults + children + babies`
  - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
  - `is_family` flag (1 if booking includes children/babies)
- Encoded categorical variables:
  - One-Hot Encoding for low-cardinality features (e.g., `meal`, `market_segment`)
  - Frequency encoding / "Other" group for high-cardinality (`country`)
- **Removed Data Leakage**  
  Dropped `reservation_status` and `reservation_status_date` (not available at prediction time).
- Final dataset split into **train/test (80/20)**.

---

