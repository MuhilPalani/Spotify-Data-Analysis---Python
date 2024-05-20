Spotify_Data_Analysis

Steps:

1. Import data
2. Analyze the data

What tools?

+ Numpy: For numerical operations and handling arrays.
+ Pandas: For data analysis and manipulation, especially for handling dataframes.

  

IMPORTING DATA

import pandas as pd  # For data manipulation and analysis
import numpy as np  # For numerical operations

# Reading the CSV file into a DataFrame
df = pd.read_csv('Spotify_data.csv')

# Displaying the shape of the DataFrame
print(df.shape)  # Shows the number of rows and columns

# Displaying basic statistics of the DataFrame
print(df.describe())  # Provides mean, std, min, max, and other statistics

# Displaying the array values of the DataFrame
print(df.values)  # Array of all the data elements


ANALYZING DATA

# Displaying column names
print(df.columns)  # Displays the headings of the columns

# Creating a new DataFrame with selected columns
df1 = pd.DataFrame(df, columns=['Track Name', 'Artist', 'Streams'])

# Displaying the new DataFrame
print(df1.head())  # Shows the first few rows of the new DataFrame

# Grouping data by artist and summing streams
artist_streams = df1.groupby('Artist')['Streams'].sum().reset_index()

# Sorting artists by the number of streams in descending order
artist_streams = artist_streams.sort_values(by='Streams', ascending=False)

# Displaying top 10 artists by streams
print(artist_streams.head(10))

VISUALIZATION

import matplotlib.pyplot as plt
import seaborn as sns

# Setting the style of the visualizations
sns.set(style="whitegrid")

# Plotting top 10 artists by streams
top_10_artists = artist_streams.head(10)
plt.figure(figsize=(12, 6))
sns.barplot(x='Streams', y='Artist', data=top_10_artists, palette='viridis')
plt.title('Top 10 Artists by Streams')
plt.xlabel('Total Streams')
plt.ylabel('Artist')
plt.show()


