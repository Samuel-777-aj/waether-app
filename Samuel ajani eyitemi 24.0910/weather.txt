document.getElementById("searchButton").addEventListener("click", () => {
    const location = document.getElementById("locationInput").value;
    const apiKey = "ddb27376819ebdc09f1e83a823d1ea3c"; // Replace with your actual API key
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${location}&appid=${apiKey}&units=metric`;

    fetch(url)
        .then(response => response.json())
        .then(data => {
            document.getElementById("location").textContent = `${data.name}, ${data.sys.country}`;
            document.getElementById("temperature").textContent = `Temperature: ${data.main.temp}°C`;
            document.getElementById("description").textContent = `Weather: ${data.weather[0].description}`;
        })
        .catch(error => {
            console.error("Error fetching weather data:", error);
            document.getElementById("location").textContent = "Could not retrieve weather data.";
            document.getElementById("temperature").textContent = "";
            document.getElementById("description").textContent = "";
        });
});
