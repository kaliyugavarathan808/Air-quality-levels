# Air-quality-levels
import pandas as pd
import numpy as np

# Define the number of rows
num_rows = 1000

# Generate random data
data = {
    "Date_Time": pd.date_range(start="2025-01-01", periods=num_rows, freq="H").strftime('%Y-%m-%d %H:%M:%S'),
    "Location": ["Coimbatore" for _ in range(num_rows)],
    "PM2.5": np.random.uniform(10, 200, num_rows),
    "PM10": np.random.uniform(20, 300, num_rows),
    "NO": np.random.uniform(0, 50, num_rows),
    "NO2": np.random.uniform(5, 100, num_rows),
    "NOx": np.random.uniform(10, 150, num_rows),
    "CO": np.random.uniform(0.1, 10, num_rows),
    "SO2": np.random.uniform(0.5, 20, num_rows),
    "O3": np.random.uniform(5, 150, num_rows),
    "Benzene": np.random.uniform(0.1, 5, num_rows),
    "Temperature": np.random.uniform(15, 40, num_rows),
    "Humidity": np.random.uniform(30, 90, num_rows),
    "Wind Speed": np.random.uniform(0.5, 15, num_rows),
    "Wind Direction": np.random.choice(["N", "S", "E", "W", "NE", "NW", "SE", "SW"], num_rows),
    "Pressure": np.random.uniform(950, 1050, num_rows),
    "AQI": np.random.randint(0, 500, num_rows)
}

# Create a DataFrame
df = pd.DataFrame(data)

# Save to CSV
df.to_csv("air_quality_data.csv", index=False)
print("Dataset created and saved as 'air_quality_data.csv'")
import pandas as pd

# Step 1: Load the dataset
file_path = "air_quality_data.csv"  # Removed the extra space in the file name
df = pd.read_csv(file_path)

# Step 2: Basic dataset overview
print("Initial shape:", df.shape)
print("\nColumn info:")
print(df.info())
print("\nMissing values:\n", df.isnull().sum())

# Step 3: Handling missing values
# Example: Drop rows with too many NaNs or fill missing values
df = df.dropna(thresh=0.7*len(df.columns))  # Drop rows with more than 30% missing
df = df.fillna(method='ffill')  # Forward fill as example (can use mean, median, etc.)

# Step 4: Fix data types (example)
# df['date'] = pd.to_datetime(df['date_column'], errors='coerce')

# Step 5: Remove duplicates
df = df.drop_duplicates()

# Step 6: Optional - Rename columns to be lowercase and replace spaces
df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')

# Step 7: Save cleaned data
cleaned_file_path = "cleaned_air_quality_data.csv"
df.to_csv(cleaned_file_path, index=False)

print("\nCleaning complete. Cleaned file saved to:", cleaned_file_path)
