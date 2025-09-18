# Binary vs Sequential Search Comparison

A comprehensive study comparing the performance of Binary Search and Sequential Search algorithms using a large retail dataset. This project demonstrates the practical differences in time complexity between O(n) and O(log n) search algorithms through real-world data analysis.

## 📋 Project Overview

This repository contains an in-depth analysis of two fundamental search algorithms:
- **Sequential Search** (Linear Search): O(n) time complexity
- **Binary Search**: O(log n) time complexity

The study uses a retail analysis dataset with over 2,000 transaction records to measure and compare the actual performance of both algorithms in both iterative and recursive implementations.

## 🗂️ Repository Structure

```
AKA-binary-sequential-search-comparison/
├── README.md                                           # This file
├── binary-vs-sequential-search-time-complexity.ipynb  # Main analysis notebook
└── data.csv                                           # Retail dataset (2000+ records)
```

## 📊 Dataset

The project uses a retail analysis dataset (`data.csv`) containing:
- **2,000+ transaction records**
- Customer information (ID, name, email, demographics)
- Transaction details (ID, date, amount, products)
- Product information (category, brand, type)
- Geographic data (city, state, country)

### Sample Data Structure
```
Transaction_ID, Customer_ID, Name, Email, Phone, Address, City, State, 
Zipcode, Country, Age, Gender, Income, Customer_Segment, Date, Year, 
Month, Time, Total_Purchases, Amount, Total_Amount, Product_Category, 
Product_Brand, Product_Type, Feedback, Shipping_Method, Payment_Method, 
Order_Status, Ratings, products
```

## 🔍 Algorithms Implemented

### 1. Sequential Search
- **Iterative Implementation**: Linear scan through data
- **Recursive Implementation**: Recursive traversal
- **Time Complexity**: O(n)
- **Space Complexity**: O(1) for iterative, O(n) for recursive

### 2. Binary Search
- **Iterative Implementation**: Iterative divide-and-conquer
- **Recursive Implementation**: Recursive divide-and-conquer  
- **Time Complexity**: O(log n)
- **Space Complexity**: O(1) for iterative, O(log n) for recursive
- **Prerequisite**: Sorted data

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.7+ installed with the following packages:

```bash
pip install pandas matplotlib jupyter time
```

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Ardavaa/AKA-binary-sequential-search-comparison.git
   cd AKA-binary-sequential-search-comparison
   ```

2. **Install dependencies** (if using pip):
   ```bash
   pip install pandas matplotlib jupyter
   ```

3. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```

4. **Open the analysis notebook**:
   Navigate to `binary-vs-sequential-search-time-complexity.ipynb`

## 💻 Usage Examples

### Running the Complete Analysis

Open the Jupyter notebook and execute all cells to:
1. Load and explore the retail dataset
2. Implement all four search algorithm variants
3. Perform time complexity measurements
4. Generate performance comparison visualizations

### Quick Example Usage

```python
# Load the dataset
import pandas as pd
df = pd.read_csv('data.csv')
transaction_ids = df['Transaction_ID'].tolist()

# Sequential Search Example
def sequential_search_iterative(data, target):
    for i in range(len(data)):
        if data[i] == target:
            return i
    return -1

# Binary Search Example (requires sorted data)
def binary_search_iterative(data, target):
    left, right = 0, len(data) - 1
    while left <= right:
        mid = (left + right) // 2
        if data[mid] == target:
            return mid
        elif data[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# Performance measurement
import time

def measure_time(search_func, data, target):
    start_time = time.time()
    result = search_func(data, target)
    end_time = time.time()
    return (end_time - start_time) * 1000000  # Convert to microseconds

# Example usage
target_id = 1000007
seq_time = measure_time(sequential_search_iterative, transaction_ids, target_id)
bin_time = measure_time(binary_search_iterative, sorted(transaction_ids), target_id)

print(f"Sequential Search Time: {seq_time:.2f} μs")
print(f"Binary Search Time: {bin_time:.2f} μs")
```

## 📈 Key Findings

The analysis demonstrates:

1. **Performance Difference**: Binary search significantly outperforms sequential search on large datasets
2. **Scalability**: The performance gap increases with dataset size
3. **Practical Impact**: For the 2000+ record dataset, binary search can be 10-40x faster
4. **Implementation Variants**: Both iterative and recursive implementations show similar performance patterns

### Sample Results
```
Case 1: Transaction_ID=1000007, Sequential Search=130.18 μs, Binary Search=3.10 μs
Case 2: Transaction_ID=1005757, Sequential Search=125.45 μs, Binary Search=2.95 μs
...
```

## 🛠️ Technical Details

### Search Algorithm Implementations

The notebook includes four complete implementations:
- `sequential_search_iterative(data, target)`
- `sequential_search_recursive(data, target, index=0)`
- `binary_search_iterative(data, target)`
- `binary_search_recursive(data, target, left=0, right=None)`

### Performance Measurement

Time measurements are conducted using Python's `time.time()` function with microsecond precision for accurate comparison of algorithm performance.

### Data Preparation

The analysis includes proper data preprocessing:
- Loading CSV data using pandas
- Converting to appropriate data structures
- Sorting data for binary search requirements
- Selecting representative test cases

## 🤝 Contributing

We welcome contributions to improve this analysis! Here's how you can contribute:

### How to Contribute

1. **Fork the repository**
2. **Create a feature branch**:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes**:
   - Add new algorithms or optimizations
   - Improve documentation
   - Add more comprehensive test cases
   - Enhance visualizations
4. **Commit your changes**:
   ```bash
   git commit -m "Add: description of your changes"
   ```
5. **Push to your branch**:
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Create a Pull Request**

### Contribution Ideas

- Add more search algorithms (Interpolation Search, Exponential Search)
- Include different datasets for comparison
- Add performance analysis for different data types
- Implement parallel search algorithms
- Add more comprehensive error handling
- Translate documentation to other languages
- Add unit tests

### Code Style

- Follow PEP 8 guidelines for Python code
- Use clear, descriptive variable names
- Add comments for complex logic sections
- Include docstrings for functions

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

- **Ardavaa** - [@Ardavaa](https://github.com/Ardavaa)

## 🙏 Acknowledgments

- Dataset sourced from Kaggle's "Retail Analysis on Large Dataset"
- Python community for excellent data analysis libraries
- Jupyter Project for the interactive notebook environment

## 📚 Educational Purpose

This project is designed for educational purposes to demonstrate:
- Algorithm analysis and comparison
- Time complexity measurement in practice
- Data structure optimization
- Python data analysis techniques
- Scientific computing with real datasets

Perfect for computer science students, data analysts, and anyone interested in understanding the practical implications of algorithm choice in data processing.

---

**Note**: The main analysis is documented in Indonesian in the Jupyter notebook, reflecting the academic context of the original study.