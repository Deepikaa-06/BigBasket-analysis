# 🛒 BigBasket Products — Exploratory Data Analysis (EDA)

A comprehensive exploratory data analysis of the BigBasket Products dataset, uncovering insights into product pricing, discount strategies, brand performance, and customer ratings across various categories.

---

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Key Steps](#key-steps)
- [Visualizations](#visualizations)
- [Key Findings](#key-findings)
- [How to Run](#how-to-run)

---

## 📌 Project Overview

This project performs an end-to-end EDA on BigBasket's product catalog to answer questions like:

- Which product categories dominate the platform?
- Which brands have the most product listings?
- How are products priced and discounted?
- What does the distribution of customer ratings look like?

---

## 📊 Dataset

| Feature | Details |
|---|---|
| **Source** | BigBasket Products CSV |
| **Total Records** | 27,555 products |
| **Columns** | 10 (index, product, category, sub_category, brand, sale_price, market_price, type, rating, description) |

### Column Descriptions

- **product** — Product name
- **category** — Main product category (e.g., Beauty & Hygiene, Gourmet & World Food)
- **sub_category** — Sub-category within the main category
- **brand** — Brand of the product
- **sale_price** — Discounted selling price (₹)
- **market_price** — Original market price (₹)
- **type** — Product type
- **rating** — Customer rating (1–5 scale)

---

## 🛠️ Technologies Used

- **Python 3**
- **Pandas** — Data manipulation and analysis
- **NumPy** — Numerical operations
- **Matplotlib** — Data visualization
- **Seaborn** — Statistical data visualization
- **Jupyter Notebook** — Interactive development environment

---

## 📁 Project Structure

```
bigbasket-eda/
│
├── BigBasket Products.csv       # Raw dataset
├── bigbasket_eda.ipynb          # Main Jupyter Notebook
└── README.md                    # Project documentation
```

---

## 🔑 Key Steps

### 1. Data Loading & Inspection
- Loaded the CSV using `pandas`
- Examined shape, data types, and basic statistics with `.info()` and `.describe()`

### 2. Missing Value Treatment

| Column | Missing Values | Treatment |
|---|---|---|
| rating | 8,636 | Filled with **median** |
| description | 115 | Column **dropped** |
| product | 1 | Filled with `"Unknown Product"` |
| brand | 1 | Filled with **mode** |
| sale_price | 6 | Filled with **median** |

### 3. Feature Engineering
- **Discount** = `market_price - sale_price`
- **Discount Percent** = `(discount / market_price) × 100`

### 4. Outlier Handling
- Used the **IQR method** on `sale_price`
- Values below `Q1 - 1.5×IQR` or above `Q3 + 1.5×IQR` were replaced with the column mean

---

## 📈 Visualizations

| Chart | Description |
|---|---|
| **Top 10 Product Categories** | Horizontal bar chart — Beauty & Hygiene leads |
| **Sale Price Distribution** | Histogram with KDE — prices concentrated below ₹400 |
| **Rating Distribution** | Histogram — most ratings cluster around 4.0–4.3 |
| **Top 10 Brands** | Bar chart — Fresho, bb Royal, and BB Home dominate |

---

## 💡 Key Findings

- **Beauty & Hygiene** is the largest category, followed by Gourmet & World Food and Kitchen, Garden & Pets
- **Fresho** is the top brand by product count (~650+ products), largely due to BigBasket's in-house label
- **Turmeric Powder** is the most listed product (26 occurrences), suggesting high demand for staples
- The **median sale price** is ₹190.32, but the mean is pulled to ₹334 by premium products — indicating a right-skewed distribution
- **Ratings** are concentrated between 3.7 and 4.3, with most products rated around 4.1
- Several products are sold **at market price** (0% discount), while others offer significant markdowns

---

## ▶️ How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/bigbasket-eda.git
   cd bigbasket-eda
   ```

2. **Install dependencies**
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook bigbasket_eda.ipynb
   ```

4. Make sure `BigBasket Products.csv` is in the same directory as the notebook.

---

## 🙌 Acknowledgements

- Dataset sourced from publicly available BigBasket product data
- Inspired by real-world e-commerce analytics use cases
