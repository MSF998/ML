- ## Downloaded the Data set from Kaggle

  - ### load the data set
    - df = pd.read_csv('Bengaluru_House_Data.csv')
    - df.info() - Provides details on the data types and column names
    - df.describe() - Talks about count, mean, std, min, max

- ## Data Cleaning

  - df.isnull().sum() - Check for missing values
  - ### Remove only rows who have less missing valus
    - df.dropna(subset=['location','size'], inplace=True)
  - ### Remove entire columns who have too many missing values
    - df.drop('society', axis=1, inplace=True)
  - ### Filling missing values for numerical columns
    - Calculate the Median
      - Median: the middle value in a dataset that is sorted from smallest to largest.
      - median_bath = df['bath'].median()
    - Fill the median value to those rows who have missing values for that column
      - df['bath'] = df['bath'].fillna(median_bath)
  - ### Filling missing values for Categorical Columns

    - For columns containing categories (like size, which might have values like '2 BHK', '3 BHK', etc.), you should use the mode.
    - Mode: The most frequently occurring value in the column.
      - mode_size = df['size'].mode()[0] #2 BHK
    - Fill the mode value where data is missing
      - df['size'] = df['size'].fillna(mode_size)

  - ### Filling missing values using Logic or a Constant Value

    - Sometimes, a missing value has an implied meaning
    - Assuming that a missing value means 0
      -missing value actually means the property has 0 balconies
    - df['balcony'] = df['balcony'].fillna(0)

  - ### Fixing Data Types
