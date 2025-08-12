import csv
import matplotlib.pyplot as plt

# Function to read weather data from CSV file
def read_weather_data(filename):
    weather_data = []
    with open(filename, 'r') as file:
        reader = csv.DictReader(file)
        for row in reader:
            data = {
                'day': row['Day'],
                'temperature': float(row['Temperature']),
                'humidity': float(row['Humidity']),
                'wind_speed': float(row['WindSpeed'])
            }
            weather_data.append(data)
    return weather_data

# Function to calculate averages
def calculate_averages(data):
    total_temp = sum([entry['temperature'] for entry in data])
    total_humidity = sum([entry['humidity'] for entry in data])
    total_wind = sum([entry['wind_speed'] for entry in data])
    count = len(data)
    return {
        'avg_temp': total_temp / count,
        'avg_humidity': total_humidity / count,
        'avg_wind': total_wind / count
    }

# Function to display weather report
def display_report(data, averages):
    print("Weather Data Report\n")
    for entry in data:
        print(f"{entry['day']} - Temp: {entry['temperature']}°C | Humidity: {entry['humidity']}% | Wind: {entry['wind_speed']} km/h")
    print("\n--- Averages ---")
    print(f"Avg Temperature: {averages['avg_temp']:.2f}°C")
    print(f"Avg Humidity: {averages['avg_humidity']:.2f}%")
    print(f"Avg Wind Speed: {averages['avg_wind']:.2f} km/h")

# Plotting graphs
def plot_graphs(data):
    days = [entry['day'] for entry in data]
    temperatures = [entry['temperature'] for entry in data]
    humidities = [entry['humidity'] for entry in data]
    wind_speeds = [entry['wind_speed'] for entry in data]

    # Line Graph
    plt.figure(figsize=(10,6))
    plt.plot(days, temperatures, marker='o', label='Temperature (°C)')
    plt.plot(days, humidities, marker='s', label='Humidity (%)')
    plt.plot(days, wind_speeds, marker='^', label='Wind Speed (km/h)')
    plt.title('Weather Data Line Graph')
    plt.xlabel('Days')
    plt.ylabel('Values')
    plt.legend()
    plt.grid(True)
    plt.show()

    # Bar Chart
    plt.figure(figsize=(10,6))
    x = range(len(days))
    plt.bar(x, temperatures, width=0.2, label='Temperature', align='center')
    plt.bar([i + 0.2 for i in x], humidities, width=0.2, label='Humidity', align='center')
    plt.bar([i + 0.4 for i in x], wind_speeds, width=0.2, label='Wind Speed', align='center')
    plt.xticks([i + 0.2 for i in x], days)
    plt.title('Weather Data Comparison (Bar Chart)')
    plt.xlabel('Days')
    plt.ylabel('Values')
    plt.legend()
    plt.show()

# Main Execution
file_name = "/content/weather_data.csv"  # Path in Google Colab
try:
    data = read_weather_data(file_name)
    averages = calculate_averages(data)
    display_report(data, averages)
    plot_graphs(data)
except FileNotFoundError:
    print(f"Error: File '{file_name}' not found.")
