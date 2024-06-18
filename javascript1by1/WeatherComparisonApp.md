17. Weather Comparison App
Description: Build an app that allows users to compare weather data for multiple cities. Skills Tested: API interaction, data visualization, DOM manipulation. Features:

Fetch weather data from a weather API for multiple cities.
Display current weather and forecast for each city.
Visualize temperature, humidity, and other metrics in a comparative chart. """ Certainly! Below is a basic version of the Weather Comparison App with some intentional mistakes for testing purposes. The application uses the OpenWeatherMap API to fetch weather data for multiple cities and displays the weather information in a simple HTML structure. The mistakes are introduced to test the interviewee's understanding of API interaction, data visualization, and DOM manipulation.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather Comparison App</title>
    <style>
        .city-weather {
            border: 1px solid #000;
            margin: 10px;
            padding: 10px;
        }
    </style>
</head>
<body>
    <h1>Weather Comparison App</h1>
    <div>
        <input type="text" id="city1" placeholder="Enter city 1">
        <input type="text" id="city2" placeholder="Enter city 2">
        <button onclick="fetchWeather()">Compare Weather</button>
    </div>
    <div id="weather-data"></div>


    <script>
        const apiKey = 'your_api_key'; // Mistake: API key is not provided.


        async function fetchWeather() {
            const city1 = document.getElementById('city1').value;
            const city2 = document.getElementById('city2').value;


            const url1 = `http://api.openweathermap.org/data/2.5/weather?q=${city1}&appid=${apiKey}`;
            const url2 = `http://api.openweathermap.org/data/2.5/weather?q=${city2}&appid=${apiKey}`;


            try {
                const response1 = await fetch(url1);
                const response2 = await fetch(url2);


                if (!response1.ok || !response2.ok) {
                    throw new Error('Failed to fetch weather data'); // Mistake: Generic error message.
                }


                const data1 = await response1.json();
                const data2 = await response2.json();


                displayWeather(data1, data2);
            } catch (error) {
                console.error(error);
                alert('Error fetching weather data'); // Mistake: Poor error handling.
            }
        }


        function displayWeather(data1, data2) {
            const weatherDataDiv = document.getElementById('weather-data');
            weatherDataDiv.innerHTML = `
                <div class="city-weather">
                    <h2>${data1.name}</h2>
                    <p>Temperature: ${(data1.main.temp - 273.15).toFixed(2)}�C</p> <!-- Mistake: Temperature conversion issue. -->
                    <p>Humidity: ${data1.main.humidity}%</p>
                </div>
                <div class="city-weather">
                    <h2>${data2.name}</h2>
                    <p>Temperature: ${(data2.main.temp - 273.15).toFixed(2)}�C</p> <!-- Mistake: Temperature conversion issue. -->
                    <p>Humidity: ${data2.main.humidity}%</p>
                </div>
            `;
        }
    </script>
</body>
</html>
Intentional Mistakes:
API Key Missing: The apiKey variable is set to a placeholder string 'your_api_key'.
Generic Error Message: The error message in the catch block is not specific, making it hard to debug.
Poor Error Handling: The alert statement for error handling is not user-friendly.
Temperature Conversion Issue: The temperature conversion from Kelvin to Celsius is not explained, and it may confuse the interviewee.
HTTP Instead of HTTPS: The API request URL uses http instead of https, which is not secure.
These mistakes will test the interviewee's ability to:

Correctly handle API keys and secure them.
Implement specific and user-friendly error handling.
Understand temperature conversion and explain it.
Use secure URLs for API requests.
The interviewee should be able to identify and correct these issues to make the app functional and user-friendly.