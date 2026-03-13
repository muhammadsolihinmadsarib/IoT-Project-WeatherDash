# WeatherDash

WeatherDash is a web-based weather monitoring and analysis dashboard developed as part of an Internet of Things (IoT) project. The system collects real-time and forecasted weather data from the Open-Meteo API and visualizes the information through an interactive web dashboard.

The platform allows users to compare forecasted and actual weather values, analyze forecast accuracy, and visualize weather data using dynamic charts and tables.



## Introduction

The integration of Internet of Things (IoT) technologies with web-based systems enables real-time data monitoring and analysis. WeatherDash is designed to demonstrate how IoT concepts can be used to build a weather monitoring dashboard that retrieves forecast and real-time weather data from external APIs.

The system visualizes weather data using interactive charts and computes forecast accuracy using statistical metrics such as Mean Squared Error (MSE).



## Objectives

The main objectives of the project are:

1. Fetch real-time and forecasted weather data such as temperature, wind speed, and precipitation using the Open-Meteo API.
2. Visualize weather information through interactive charts and tables.
3. Compute forecast error metrics such as Mean Squared Error (MSE).
4. Provide an accessible web-based platform that requires no installation.
5. Minimize system complexity and development cost by avoiding physical sensor hardware.



## Problem Statement

Most weather platforms provide forecast data but do not allow users to evaluate the accuracy of those predictions once the weather has occurred. This limitation makes it difficult for users to assess the reliability of forecasts.

WeatherDash addresses this problem by comparing forecasted and actual weather data retrieved from the Open-Meteo API. The system calculates forecast accuracy using statistical methods and presents the results through visual dashboards.



## System Architecture

WeatherDash follows a client-server architecture.

The frontend interacts with a backend server through RESTful APIs. The backend retrieves weather data from an external API, stores the data in a database, performs analysis, and sends the processed data back to the frontend for visualization.

```
User Browser
      |
      v
Frontend Dashboard (HTML / CSS / JavaScript)
      |
      v
Flask Backend Server
      |
      v
SQLite Database
      |
      v
Open-Meteo Weather API
```



## Technologies Used

| Category | Technology |
|--------|--------|
| API | Open-Meteo Weather API |
| Backend | Python Flask |
| Database | SQLite |
| Frontend | HTML5, CSS3, JavaScript |
| Data Visualization | Chart.js |
| Table Visualization | DataTables |



## Data Flow

1. The system starts when the Flask application (`app.py`) is executed.
2. A data collection module retrieves forecast and real-time weather data from the Open-Meteo API.
3. The retrieved data is processed and stored in a local SQLite database.
4. The backend calculates forecast accuracy metrics such as Mean Squared Error (MSE).
5. The frontend dashboard retrieves processed data through API endpoints.
6. Charts and tables are dynamically rendered for user interaction.



## Database Design

WeatherDash uses a lightweight SQLite database named `weather_data.db`.

### Table Schema

```
CREATE TABLE IF NOT EXISTS weather_data (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    timestamp TEXT,
    forecast_temp REAL,
    actual_temp REAL,
    forecast_wind REAL,
    actual_wind REAL
);
```

### Stored Data

| Column | Description |
|------|------|
| id | Unique identifier for each record |
| timestamp | Date and time of the recorded data |
| forecast_temp | Forecasted temperature |
| actual_temp | Actual measured temperature |
| forecast_wind | Forecasted wind speed |
| actual_wind | Actual wind speed |


## Forecast Accuracy Evaluation

The system evaluates forecast accuracy using **Mean Squared Error (MSE)**.  

MSE quantifies how close predicted values are to the actual values by averaging the squared differences:

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

Where:  
- \( n \) = number of observations  
- \( y_i \) = actual value at observation \( i \)  
- \( \hat{y}_i \) = predicted value at observation \( i \)  

You can also include **Root Mean Squared Error (RMSE)** for a more interpretable metric:

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2}
$$

For percentage-based error, **Mean Absolute Percentage Error (MAPE)** is useful:

$$
\text{MAPE} = \frac{100\%}{n} \sum_{i=1}^{n} \left| \frac{y_i - \hat{y}_i}{y_i} \right|
$$

These metrics provide a comprehensive view of forecast accuracy.

Where:

- yi = actual value  
- ŷi = predicted value  
- n = total observations  

Two types of metrics are calculated:

- Overall MSE for temperature and wind speed
- Daily MSE grouped by date



## Data Visualization

The dashboard includes several visualization components:

Temperature Comparison Graph
- Line charts comparing forecasted and actual temperature.

Wind Speed Comparison
- Charts showing differences between predicted and actual wind speed.

Error Metrics
- Displays MSE values for evaluating forecast accuracy.

Interactive Interface
- Users can select parameters and dates to update the displayed charts.



## Installation

Clone the repository:

```
git clone https://github.com/muhammadsolihinmadsarib/IoT-Project-WeatherDash.git
```

Navigate to the project directory:

```
cd IoT-Project-WeatherDash
```

Install required dependencies:

```
pip install -r requirements.txt
```

Run the application:

```
python app.py
```

The dashboard can then be accessed through the browser.



## Conclusion

WeatherDash demonstrates the practical application of IoT concepts through a fully software-based weather monitoring system. The platform integrates real-time weather data retrieval, database storage, statistical analysis, and interactive visualization.

By comparing forecasted and actual weather values, the system enables users to evaluate forecast accuracy and better understand weather prediction reliability.



## License

This project is licensed under the MIT License.
