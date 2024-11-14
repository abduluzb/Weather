const apiKey = '1ad5662fcef05082a9243e654ee2dc41';  // Получите ключ от OpenWeatherMap

document.getElementById('getWeatherBtn').addEventListener('click', async () => {
    const city = document.getElementById('city').value;
    if (!city) {
        alert('Введите название города!');
        return;
    }

    const weatherData = await getWeather(city);
    if (weatherData) {
        displayWeather(weatherData);
    }
});

async function getWeather(city) {
    const response = await fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric&lang=ru`);
    const data = await response.json();

    if (data.cod === '404') {
        alert('Город не найден!');
        return null;
    }

    return {
        cityName: data.name,
        temperature: data.main.temp,
        description: data.weather[0].description
    };
}

function displayWeather(data) {
    document.getElementById('cityName').textContent = data.cityName;
    document.getElementById('temperature').textContent = `${data.temperature}°C`;
    document.getElementById('weatherDescription').textContent = data.description;
}
