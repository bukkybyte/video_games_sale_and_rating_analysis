# Video Game Data Analysis

This project focuses on analyzing a dataset of video games, exploring various aspects such as **Critic Scores**, **User Scores**, **Sales by Region**, and more. The goal is to clean, explore, and analyze the data to uncover insights, patterns, and trends within the video game industry. Additionally, visualizations are created to make the findings easier to interpret.

## Table of Contents
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Setup and Installation](#setup-and-installation)
- [Usage](#usage)
- [Data Processing Steps](#data-processing-steps)
  - [Upload Dataset](#upload-dataset)
  - [Import Libraries](#import-libraries)
  - [Data Exploration](#data-exploration)
  - [Data Cleaning](#data-cleaning)
  - [Data Analysis](#data-analysis)
  - [Visualization](#visualization)
- [Contributors](#contributors)

## Project Overview
This project analyzes a dataset of video games to gain insights into various aspects of the gaming industry. Key areas of focus include:
- **Critic and User Scores**: Comparing how critics and users rate video games.
- **Sales by Region**: Understanding the geographic distribution of video game sales.
- **Genre and Platforms**: Analyzing the relationship between game genre, platform, and success.
- **Data Visualizations**: Generating clear, insightful visualizations to summarize findings.

## Data Source
The data used in this project comes from publicly available video game datasets on [Kaggle](https://www.kaggle.com/datasets/thedevastator/video-game-sales-and-ratings). It includes columns like:
- `Game Title`
- `Platform`
- `Genre`
- `Critic Score`
- `User Score`
- `Sales by Region` (NA, EU, JP, Other)
- `Year of Release`

This data is included in the repository or referenced from the source.

## Setup and Installation

### Prerequisites
- Python 3.x
- Git
- Required Python libraries (listed in `requirements.txt`)

### Installation Steps
1. Clone the repository:
    ```bash
    git clone https://github.com/bukkybyte/video_games_sale_and_rating_analysis.git
    ```

2. Navigate to the project directory:
    ```bash
    cd video_games_sale_and_rating_analysis
    ```

3. Install the required dependencies:
    ```bash
    pip install -r requirements.txt
    ```

4. Make sure you have Jupyter Notebook or a Python IDE to run the analysis scripts.

## Usage

1. **Upload Dataset**: Load the dataset using Pandas, either from a `.csv` file or any other suitable format.

2. **Import Libraries**: Libraries like Pandas, Matplotlib, and Seaborn are used for data manipulation and visualization.

3. **Run the Analysis**: You can run the analysis in Jupyter Notebook or by executing the Python scripts:
    ```bash
    python video_games.ipynb
    ```

   The notebook/script will process the dataset, clean the data, and generate visualizations.

## Data Processing Steps

### Upload Dataset
The first step involves loading the dataset into the environment for analysis. The dataset is typically in `.csv` format, and is loaded using Pandas:
```python
import pandas as pd
df = pd.read_csv('Video_Games.csv')
```

### Import Libraries
We use essential libraries for data analysis and visualization:
```python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import plotly.io as pio
from sklearn.preprocessing import LabelEncoder # Encode features to make them numerical for Ml or statistical analysis

# Set renderer for troubleshooting
pio.renderers.default = "browser"  # Use "notebook" for Jupyter

pd.options.mode.chained_assignment = None  # default='warn'
```

### Data Exploration
Exploring the data is the first step to understand its structure and content. This includes inspecting the first few rows, checking for missing values, and summarizing key statistics:
```python
df.head()       # Display the first few rows
df.info()       # Get info about the dataset (data types, missing values)
```

### Data Cleaning
This step involves cleaning the data to ensure it's ready for analysis:
- **Handling Missing Values**: Replacing or removing NaNs.
- **Removing Duplicates**: Ensuring no duplicate rows.
- **Fixing Data Types**: Converting columns to the appropriate data types.
- **Handling Incorrect or Outlier Data**: For example, replacing 'tbd' values in `User Score` with NaN.

```python
df['User_Score'] = pd.to_numeric(df['User_Score'], errors='coerce')  # Convert 'User_Score' to numeric
df.drop_duplicates(inplace=True)  # Drop duplicates
```

### Data Analysis
Once the data is cleaned, we perform various analyses to uncover insights:
- **Correlation Analysis**: Comparing how different features relate to one another.
- **Sales by Region**: Grouping sales by region and genre.
- **Comparison of Critic and User Scores**: Checking for correlations between critic and user ratings.

Example code for calculating correlation:
```python
corr_matrix = df[['Critic_Score', 'User_Score', 'NA_Sales', 'EU_Sales']].corr()
print(corr_matrix)
```

### Visualization
Visualizations help to communicate insights more effectively. Some common visualizations in this project include:
- **Bar Charts**: Showing sales by region and genre.
- **Scatter Plots**: Displaying the relationship between critic and user scores.
- **Correlation Matrix**: A heatmap showing correlations between variables.

Example of a bar plot for sales by region and genre:
```python
region_genre_sales = df.groupby('Genre')[['NA_Sales', 'EU_Sales', 'JP_Sales', 'Other_Sales']].sum()
region_genre_sales.plot(kind='bar', figsize=(12, 6))
plt.title("Video Games Sales by Genre and Region")
plt.xlabel("Genre")
plt.ylabel("Sales (in millions)")
plt.xticks(rotation=45)
plt.show()
```


## Contributors

- [Taofeeq Nurudeen](https://github.com/bukkybyte) - Project Lead and Developer

---

This **README.md** template covers the complete workflow of your project from uploading the dataset to performing analysis and visualization. Feel free to tweak it further based on any specific details or changes to your project!
