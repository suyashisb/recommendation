# Product Recommendation System

## Overview
This project implements a product recommendation engine using association rule mining (Apriori algorithm) on historical order data.

## Features
- **Association Rule Mining**: Uses mlxtend library to discover frequent itemsets and association rules
- **Basket Recommendations**: Generates personalized product recommendations for each customer order
- **SKU-Based Recommendations**: Parallel implementation using product SKU identifiers
- **Name-Based Recommendations**: Implementation using product names
- **Submission Format**: Generates formatted output files for evaluation

## Data Files
- `all_except_last_orders.csv` - Historical order data for rule mining (training data)
- `last_orders_subset.csv` - Recent orders for generating recommendations (test data)

## Output Files
- `associationrules.csv` - Generated association rules with confidence and lift metrics
- `associationrules_sku.csv` - Association rules using SKU identifiers
- `basket_recommendations.csv` - Detailed recommendations with product names
- `basket_recommendations_sku.csv` - Detailed recommendations with SKU identifiers
- `submission.csv` - Final submission format: ID, Order, SKU, Member, ProductName

## Notebooks
- `association.ipynb` - Name-based recommendation pipeline
- `association_sku.ipynb` - SKU-based recommendation pipeline

## Recommendation Algorithm
1. **Data Preparation**: Create transaction matrix from historical orders
2. **Frequent Itemset Mining**: Apply Apriori algorithm (min_support=0.002-0.03)
3. **Association Rules**: Generate rules using confidence metric (min_threshold=0.6)
4. **Inverted Index**: Create efficient lookup structure for relevant rules
5. **Recommendation Generation**: Extract top 5 unique products per order
6. **Fallback Logic**: Use global popular products for orders without matched rules

## Results
- **Total Recommendations**: 3,190 (638 orders × 5 unique items per order)
- **Performance**: Optimized with inverted index for O(1) rule lookups
- **Code Quality**: Descriptive naming conventions, no comments for clean readability

## Dependencies
- pandas
- mlxtend (apriori, association_rules)
- sortedcontainers
- Python 3.7+

## Installation
```bash
pip install pandas mlxtend sortedcontainers
```

## Usage
Run the Jupyter notebooks in sequence:
1. Execute cells in `association.ipynb` or `association_sku.ipynb`
2. Review generated CSV files for results
3. Use `submission.csv` for evaluation submission

## Author
Suyashi SB

## License
MIT
