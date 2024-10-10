# Data Cleaning with Python
## Project overview
This project demonstrates effective techniques for cleaning and preparing data using Python, with a focus on NumPy and Pandas libraries. It processes three different datasets, showcasing various data cleaning methods.

## Project Structure
```
data-cleaning-python/
│
├── Datasets/
│   ├── BL-Flickr-Images-Book.csv
│   ├── olympics.csv
│   └── university_towns.txt
│
├── Output/
│   └── .gitkeep
│   
├── .gitignore
├── README.md
├── requirements.txt
└── winston_wolfe.py
```

## Features

- Cleaning and normalizing text data
- Handling dates and time series
- Removing duplicates and incomplete records
- Transforming categorical data
- Dealing with missing values

## Setup and Run

1. Clone the repository:
```
git clone https://github.com/1gorb1lyk/data-cleaning-python.git
```
2. Install the required dependencies:
```
pip install -r requirements.txt
```
3. Run the data cleaning script:
```
python winston_wolfe.py
```

## Usage Example
### Cleaning Book data
```
import pandas as pd

df = pd.read_csv('Datasets/BL-Flickr-Images-Book.csv')
df = df.set_index('Identifier')
df = df.drop(['Edition Statement', 'Corporate Author', 'Corporate Contributors'], axis=1)
```

### Processing Publication Dates
```
import numpy as np

df['Date of Publication'] = pd.to_numeric(df['Date of Publication'].str.extract(r'^(\d{4})', expand=False))
```

### Normalizing Publication Places
```
london = df['Place of Publication'].str.contains('London')
oxford = df['Place of Publication'].str.contains('Oxford')
df['Place of Publication'] = np.where(london, 'London',
                                      np.where(oxford, 'Oxford',
                                               df['Place of Publication'].str.replace('-', ' ')))
```

### Datasets
1. BL-Flickr-Images-Book.csv: A dataset containing information about books.
2. olympics.csv: A dataset with information about Olympic Games.
3. university_towns.txt: A text file containing information about university towns.
