# Football-Players-Exploratory-Data-Analysis
This Project provides an insightful analysis into the world of football by leveraging a dataset of player attributes and performances. Key features of the analysis include:

Data Preparation and Overview: Initial steps involve importing necessary libraries such as NumPy, pandas, matplotlib, and seaborn. The dataset, presumably containing detailed attributes of football players, is loaded for exploration.

Player Search: A specific example shows how to search for a player by name (e.g., Cristiano Ronaldo) and retrieve relevant information such as nationality, wage, value, skill moves, and overall rating.

Distribution Analysis: The notebook presents a statistical distribution of players' overall ratings, highlighting the mean and median values with visual aids. This analysis offers insights into the general performance levels within the dataset.

Top Performers Identification: A segment is dedicated to identifying the top players based on their overall ratings, showcasing attributes such as name, age, nationality, wage, value, and position.

This structured approach not only reveals the dataset's underlying patterns and player rankings but also demonstrates the application of data visualization techniques to enhance understanding and presentation of football analytics.


## Datasets
Data set contains information about football player, data set is collected from various kaggle public posts and is combined together.


## Exploratory Data Analysis
Exploratory Data Analysis on this data set provides us great insight about the football players which can help in creating a great team for match.

## Technical Information

The data is first cleaned and processed for easier processing.
Once the data is processed we use different techniques to bring the data into Normal distribution, this helps in better decision making.

We are the visualizing the data for different parameters to obtaint the relationship among them.

### 1. Importing Libraries
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
```
This step involves importing necessary Python libraries for data manipulation and visualization:
- **NumPy** (`numpy`): Used for numerical computations.
- **pandas** (`pd`): Provides data structures and functions for effective data manipulation and analysis.
- **matplotlib** (`plt`): A plotting library for creating static, animated, and interactive visualizations in Python.
- **seaborn** (`sns`): Based on matplotlib, seaborn facilitates the creation of informative and attractive statistical graphics.

### 2. Loading the Data
```python
data = pd.read_csv("players_data.csv")
data.head()
```
Here, the pandas library is used to load a CSV file named `"players_data.csv"`, which likely contains information about football players. The `.head()` function displays the first few rows of the dataframe, providing a glimpse into the dataset's structure and the type of information it contains (e.g., player names, nationalities, wages, values, etc.).

### 3. Searching for a Specific Player
```python
player = 'Cristiano Ronaldo'
data[data.Name.str.contains(player)].get(["Name", "Nationality", "Wage", "Value", "Skill Moves", "Overall"])
```
This code snippet demonstrates how to search for a specific player (in this case, Cristiano Ronaldo) within the dataset. It filters the rows where the player's name matches the given string and retrieves selected columns such as Name, Nationality, Wage, Value, Skill Moves, and Overall rating.

### 4. Distribution Analysis of Player Ratings
```python
sns.displot(data.Overall, kind='kde', fill=True, rug = True)

plt.axvline(data.Overall.mean(), color='green', label='Mean')
plt.axvline(data.Overall.median(), color='orange', label='Median')
```
Using seaborn, this part of the code creates a distribution plot (Kernel Density Estimate - KDE) for the players' overall ratings, with the distribution filled in and a 'rug' plot on the axis to indicate individual data points. It also marks the mean and median of the overall ratings on the plot with vertical lines in green and orange, respectively, providing insights into the distribution's central tendency.

### 5. Identifying Top Players
```python
print('Top players are:')
percentile = 100-0.06
quantile=percentile/100
data[data.Overall > data.Overall.quantile(quantile)].get(["Name", "Age", "Nationality", "Wage", "Value", "Position", "Overall"])
```
This segment calculates a high percentile (essentially identifying the top 0.06% of players based on their Overall rating) and filters the dataset to only include players above this threshold. It then retrieves information about these top players, such as their Name, Age, Nationality, Wage, Value, Position, and Overall rating, effectively highlighting the elite performers in the dataset.

---
### 1. Data Cleaning and Preprocessing
- **Handle Missing Values**: Investigate and handle missing or null values in the dataset, either by filling them with appropriate values (mean, median, mode) or by removing the rows/columns with missing data, depending on the context.
- **Data Type Conversion**: Ensuring that the data types of each column are appropriate for the data they contain. For example, converting categorical variables that are encoded as strings into numeric codes or one-hot encoded vectors.

### 2. Feature Engineering
- **Create New Features**: Derive new variables that might be more informative for analysis. For instance, creating a "Value-to-Wage Ratio" might provide insights into which players offer the best value for money.
- **Categorize Players**: Group players into categories (e.g., "High Potential", "Veteran", "Rising Star") based on certain criteria like age, overall rating, and growth potential. This can help in performing targeted analyses on specific groups.

Finally we move forward with the correlation of the main features among them.

The Box plot for different features helps us in determining the adequate players and the outliers

