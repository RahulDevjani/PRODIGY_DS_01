import pandas as pd
import matplotlib.pyplot as plt

# Load the data
url = '/content/API_SP.POP.TOTL_DS2_en_csv_v2_45183.csv'
data = pd.read_csv(url, skiprows=4)

# Filter for the most recent year (2022)
most_recent_year = '2022'
recent_data = data[['Country Name', most_recent_year]].dropna()

# Sort by population and take the top 20 for better visualization
recent_data = recent_data.sort_values(by=most_recent_year, ascending=False).head(20)

# Plot the bar chart
plt.figure(figsize=(12, 8))
plt.barh(recent_data['Country Name'], recent_data[most_recent_year].astype(float))
plt.xlabel('Total Population')
plt.title('Top 20 Countries by Total Population in 2022')
plt.gca().invert_yaxis()
plt.show()
