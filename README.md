# Categorical-Data-Analaysis-using-Python
# Theory:
This experiment demonstrates basic techniques for analyzing **categorical data** using Pandas in Python. Categorical data consists of variables that represent discrete groups or categories (e.g., gender, department, grade, payment method) rather than continuous numerical values.

The notebook covers essential methods for understanding, summarizing, and exploring categorical variables:

1. Creating a small sample DataFrame with categorical columns  
   ```python
   import pandas as pd

   data = {
       'Order_ID': ['01','02','03','04','05','06','07','08','09'],
       'Category': ['electronics','clothing','grocery','electronics','clothing','grocery','clothing','electronics','grocery'],
       'Payment_Method': ['UPI','COD','UPI','COD','UPI','COD','UPI','COD','UPI'],
       'Delivery_type': ['Standard','Express','Standard','Express','Standard','Express','Standard','Express','Standard'],
       'Customer_Type': ['Regular','New','Regular','New','Regular','New','Regular','New','Regular']
   }

   df = pd.DataFrame(data)
   ```

2. Frequency count of each category  
   ```python
   df['Category'].value_counts()
   ```

3. Getting unique values  
   ```python
   df['Category'].unique()
   ```

4. Number of unique categories  
   ```python
   df['Category'].nunique()
   ```

5. Percentage distribution (proportions)  
   ```python
   df['Category'].value_counts(normalize=True) * 100
   ```

6. Cross-tabulation (contingency table)  
   ```python
   pd.crosstab(df['Category'], df['Payment_Method'])
   pd.crosstab(df['Delivery_type'], df['Customer_Type'])
   ```

7. Filtering rows for a specific category  
   ```python
   electronics_orders = df[df['Category'] == 'electronics']
   ```

8. Grouping and counting  
   ```python
   df.groupby('Category')['Order_ID'].count()
   ```

9. Sorting data by categorical column  
   ```python
   df.sort_values(by='Category')
   ```

10. Loading a larger real dataset and performing similar categorical analysis  
    ```python
    df = pd.read_csv('Expt11.csv')

    # Examples from student dataset:
    df['Grade'].value_counts()
    df['Grade'].value_counts(normalize=True) * 100
    df['Department'].value_counts()
    df['Gender'].value_counts()
    pd.crosstab(df['Gender'], df['Grade'])
    pd.crosstab(df['Department'], df['Gender'])
    pd.crosstab(df['Department'], df['Grade'], normalize='index') * 100
    df.groupby('Department')['Grade'].value_counts()
    ```

These methods are fundamental for:
- Understanding distribution of categories
- Identifying relationships between categorical variables
- Summarizing patterns in survey data, customer data, student records, sales data, etc.

## Conclusion

The experiment successfully showed how to:
- Create and inspect small categorical datasets
- Compute frequency counts, unique values, and percentages
- Build cross-tabulations to analyze relationships between two categorical variables
- Filter, group, and sort categorical data
- Apply the same techniques to a larger student performance dataset (60 records)

Key observations from the student dataset:
- Balanced gender distribution (30 male, 30 female)
- CSE has the highest number of students (20)
- Grade B is the most common (40%)
- CSE students perform best in terms of Grade A percentage (~65%)
- Mechanical department has no Grade A students
