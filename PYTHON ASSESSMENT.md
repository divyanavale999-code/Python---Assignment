#### Section A: Concept Application





1\. Identify the string methods and their execution order needed to remove extra spaces and fix inconsistent casing in a product name.



\->  To fix inconsistent casing and remove extra spaces in a product name, you need to execute string methods in a specific sequence: trimming, normalizing spaces, and fixing the case.



**Remove leading/trailing spaces:** .trim()Action: Removes accidental spaces at the very beginning or end of the product name.



**Remove extra consecutive spaces:** .split(" ") and .join(" ") (or .replaceAll("  ", " "))Action: Collapses multiple, consecutive spaces down to a single space.



**Fix inconsistent casing:** .toLowerCase() or .toUpperCase() (or .capitalize())Action: Converts the entire string to a uniform casing.  





2\. Explain why manual CSV loading often treats numeric columns as strings and identify the function used to convert them to floats.



\->  Manual CSV loading treats numeric columns as strings because the CSV file format does not store data type metadata.





3\. Determine the best data structure for mapping product names to total sales and explain the drawback of using a list instead.



\->  The best data structure for mapping product names to total sales is a dictionary in Python.





4\. Compare using a manual for loop versus the sum() function, identifying a scenario where the loop is the only viable option.



\->  Both a manual for loop and the built-in sum() function can calculate totals, but they differ in flexibility and use cases.



&#x20;   Using sum() :- The sum() function is shorter and faster for simple numeric addition.





5\. Describe how to implement type checking or error handling to prevent a TypeError when comparing a potential string variable to a number.



\->  To prevent a TypeError when comparing a potential string to a number in Python, you must ensure both values share compatible data types before executing the comparison.Here is how to implement type checking and error handling to handle this safely.





6\. Explain the benefits of modularizing a data pipeline into separate functions and the risks of using a single large code block in analytics.



\->  Modularizing a data pipeline means breaking code into small, isolated functions. Keeping all code in one large block creates significant technical debt.



**#  Benefits of Modular Functions**



* Easier Debugging: You isolate errors to specific functions quickly.



* Code Reusability: You write logic once and reuse it across pipelines.



* Simplified Testing: You can write unit tests for individual steps.



* Better Collaboration: Multiple developers can work on different functions simultaneously.



* Clearer Readability: Small functions act as self-explaining documentation.



* Flexible Scaling: You can update one component without breaking others.





#### Section B: Practical Task





1\. Load the sales\_data\_sample.csv file and use Python string methods to trim whitespace and apply title casing to the 'PRODUCTLINE' column.



import pandas as pd



\# Load the CSV file

df = pd.read\_csv("sales\_data\_sample.csv")



\# Clean the PRODUCTLINE column

df\["PRODUCTLINE"] = (

&#x20;   df\["PRODUCTLINE"]

&#x20;   .str.strip()      # Remove leading/trailing whitespace

&#x20;   .str.title()      # Convert to title case

)



\# Display updated column

print(df\["PRODUCTLINE"].head())





2\. Iterate through the 'SALES' column to remove non-numeric characters and cast the cleaned values into a float data type.



import pandas as pd

import re



\# Load CSV file

df = pd.read\_csv("sales\_data\_sample.csv")



\# Clean and convert SALES column

cleaned\_sales = \[]



for value in df\["SALES"]:

&#x20;   # Convert value to string and remove non-numeric characters

&#x20;   cleaned\_value = re.sub(r"\[^0-9.]", "", str(value))

&#x20;   

&#x20;   # Convert cleaned value to float

&#x20;   cleaned\_sales.append(float(cleaned\_value))



\# Assign cleaned float values back to the column

df\["SALES"] = cleaned\_sales



\# Verify result

print(df\["SALES"].head())

print(df\["SALES"].dtype)





3\. Construct a dictionary where each key is a unique 'PRODUCTLINE' and the value is the cumulative sum of 'SALES' for that category.



import pandas as pd



\# Load CSV file

df = pd.read\_csv("sales\_data\_sample.csv")



\# Create dictionary for cumulative sales by PRODUCTLINE

product\_sales = {}



for index, row in df.iterrows():

&#x20;   product = row\["PRODUCTLINE"]

&#x20;   sales = float(row\["SALES"])



&#x20;   # Add sales to existing total or initialize new key

&#x20;   if product in product\_sales:

&#x20;       product\_sales\[product] += sales

&#x20;   else:

&#x20;       product\_sales\[product] = sales



\# Display result

print(product\_sales)





4\. Use a loop and conditional logic to categorize product lines as "High Revenue Product" if total sales exceed 100,000, printing the results to the console.



\# Dictionary containing product lines and their total sales

product\_sales = {

&#x20;   "Electronics": 250000,

&#x20;   "Clothing": 85000,

&#x20;   "Home Goods": 110000,

&#x20;   "Toys": 45000

}



\# Loop through the product lines to evaluate sales

for product, sales in product\_sales.items():

&#x20;   if sales > 100000:

&#x20;       category = "High Revenue Product"

&#x20;   else:

&#x20;       category = "Standard Product"

&#x20;       

&#x20;   print(f"{product}: ${sales:,} - {category}")





