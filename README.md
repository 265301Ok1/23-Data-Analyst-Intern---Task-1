# 23-Data-Analyst-Intern---Task-1
This repository is about cleaning of Sales_Data_Sample gotten from kaggle.com. I used Python(Pandas) to drop rows that are null after checking they are empty. Removed duplicates and as well standardize texts, ensuring dates are formatted to datetime dataframe. I ensure all the headers are in lowercase for uniformity and proper data type was done.

**I Imported Sales_Data_Sample in Python Using**

df = pd.read_csv(
    r"C:\Users\user\Desktop\DATA ANALYSIS\23 Data Analyst Internship\sales_data_sample.csv",
    encoding='latin1'
)
To be sure it is properly loaded 

**I run this command** 
print(df.head())

To identify missing values, I ran 

**Check for missing values in each column**
print(df.isnull().sum())

**To view rows missing values**

missing_rows = df[df.isnull().any(axis=1)]

print(missing_rows)

**To Check if Any Missing Values Exist**

print(df.isnull().values.any())
This return true

**Remove rows with missing values**

missing_rows = df[df.isnull().any(axis=1)]
print(missing_rows)

It was observed that some sales figure were missing and needed to be replaced I used mean function to replace anout 147 cells using

**Fill missing numeric values with mean**

df['SALES'] = df['SALES'].fillna(df['SALES'].mean())

**Fill missing categorical values with mode**

df['STATUS'] = df['STATUS'].fillna(df['STATUS'].mode()[0])

I used mode to fill cell that appeared NaN

**Confirm missing values handled**
print(df.isnull().sum())

I checked if there are missing data, it all returned to be okay.

I observed there is significant empty value in ADDRESSLINE2 and for such it is not important, I opted to DROP it

**Because there are too many missing value in ADDRESSLINE2 drop function is used**
df = df.drop('ADDRESSLINE2', axis=1)

**Standardization** 

There is inconsistency in country column so Converted all to capital letter with this command

**# To correct inconsistency in data entry**
df['COUNTRY'] = df['COUNTRY'].str.upper()

**Because there are too many missing value in STATE drop function is used**
df = df.drop('STATE', axis=1)

**Check if STATE columns is deleted**
print(df.columns)

**Convert ORDERDATE to datetime**
df['ORDERDATE'] = pd.to_datetime(df['ORDERDATE'])

**Change format to DD-MM-YYYY**
df['ORDERDATE'] = df['ORDERDATE'].dt.strftime('%d-%m-%Y')

**To check the result**
print(df['ORDERDATE'].head())

**T To structure Orderdate in dd-mm-yyyy**

**Convert ORDERDATE to datetime**
df['ORDERDATE'] = pd.to_datetime(df['ORDERDATE'])

**Convert ORDERDATE to datetime**
df['ORDERDATE'] = pd.to_datetime(df['ORDERDATE'])

**Change format to DD-MM-YYYY**
df['ORDERDATE'] = df['ORDERDATE'].dt.strftime('%d-%m-%Y')

**To check if date has been converted**
print(df['ORDERDATE'])

**Checking data type**
print(df.dtypes)

Since Orderdate still remain Object which is string it will be converted to datetime by using the command below

## Convert date column
df['orderdate'] = pd.to_datetime(
    df['orderdate'],


    format='%d/%m/%Y'
)

**Checking data type again**
print(df.dtypes)
