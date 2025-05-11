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
