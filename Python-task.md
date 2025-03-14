# task 1: System Monitoring Script
 *📌 Task: Use an appropiate Python library to display CPU and memory usage.*
  *✅ Instructions:*

 *Install python lib using pip.*

 *Write a script that prints CPU and memory usage every few seconds.*

*Example output:*
*CPU Usage: 35% Memory Usage: 60%*

*Bonus: Extend the script to log this data into a file for future analysis.*

# System Monitoring Script

```bash
pip apt install python pip
```
![](https://raw.githubusercontent.com/cliuzy/Team-collaboration/main/images/Sc2.png)

```nano
 nano system_monitor.py
```
![](https://raw.githubusercontent.com/cliuzy/Team-collaboration/main/images/Sc3.png)

Now, run the script:

```bash
python3 system_monitor.py
```
It should start printing system usage like this:


![](https://raw.githubusercontent.com/cliuzy/Team-collaboration/main/images/Sc4.png)
___

# Task 2
API Interaction (Weather Data Fetching)
📌 Task: Write a Python script that fetches weather data from an API and processes the response.
✅ Instructions:

Sign up at OpenWeatherMap and get a free API key.

Fetch weather details (temperature, weather condition, humidity) for a given city.

Example output:
Weather in Lagos: Temperature: 30°C Condition: Clear sky Humidity: 75%

Bonus: Modify the script to allow users to enter multiple city names.
___
Get an OpenWeatherMap API Key
Go to OpenWeatherMap and create an account.
Navigate to API Keys and generate a free API key.
Copy the API key for use in the script.

*You'll need the requests library to make API calls:*
```bash
pip3 install request
```
Create the Weather Fetching Script
Save the following script as weather_fetch.py:

```python
import requests

# Replace with your actual API key
API_KEY = "your_api_key_here"
BASE_URL = "http://api.openweathermap.org/data/2.5/weather"

def get_weather(city):
    """Fetch weather data for a given city"""
    params = {
        "q": city,
        "appid": API_KEY,
        "units": "metric"  # Convert temperature to Celsius
    }
    
    response = requests.get(BASE_URL, params=params)
    
    if response.status_code == 200:
        data = response.json()
        temperature = data["main"]["temp"]
        condition = data["weather"][0]["description"]
        humidity = data["main"]["humidity"]
        
        print(f"Weather in {city}: Temperature: {temperature}°C Condition: {condition.title()} Humidity: {humidity}%")
    else:
        print(f"Failed to get weather data for {city}. Check city name or API key.")

def main():
    """Allow user to enter multiple cities"""
    cities = input("Enter city names separated by commas: ").split(",")

    for city in cities:
        get_weather(city.strip())  # Remove extra spaces

if __name__ == "__main__":
    main()
```
Run the script
```bash
python3 weather_fetch.py
```
___

# 📌 Task 3: 
### Write a script that scans a .log file and counts occurrences of the word "ERROR".
✅ Instructions:

Create a sample .log file with different log messages, including "ERROR".

Write a Python script that reads the file and counts occurrences of "ERROR".

Example output:
Found 5 occurrences of 'ERROR' in logs.

Bonus: Extend the script to filter logs by date or severity level (INFO, WARNING, ERROR).
___

📌 Step 1: Create a Sample Log File
Create a file called sample.log and add some logs:

```bash
touch sample.log
```
add this to the file

```bash
2024-03-13 12:00:01 - INFO - System started
2024-03-13 12:05:32 - WARNING - High memory usage detected
2024-03-13 12:10:15 - ERROR - Failed to connect to database
2024-03-13 12:15:45 - INFO - User logged in
2024-03-13 12:20:50 - ERROR - Timeout while fetching API data
2024-03-13 12:30:10 - ERROR - Disk space low
```
Create a file called log_scanner.py and add this script:

```python

import re

LOG_FILE = "sample.log"

def count_errors(log_file):
    """Counts occurrences of 'ERROR' in the log file."""
    error_count = 0
    with open(log_file, "r") as file:
        for line in file:
            if "ERROR" in line:  # ✅ Indentation fixed
                error_count += 1  # ✅ Valid statement
    return error_count

if __name__ == "__main__":
    error_count = count_errors(LOG_FILE)
    print(f"Found {error_count} occurrences of 'ERROR' in logs.")
```
Run your script again:
```bash

python3 log_scanner.py
```
we have somthing like this
![](https://raw.githubusercontent.com/cliuzy/Team-collaboration/main/images/Sc7.png)
