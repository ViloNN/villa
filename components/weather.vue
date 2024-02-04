<template>
  <div
    class="min-h-[36rem] bg-blue-100 flex flex-col justify-start items-center p-4 pt-36"
  >
    <div
      class="flex flex-col md:flex-row space-y-4 md:space-y-0 md:space-x-4 w-full max-w-6xl"
    >
      <!-- Karta z aktualną pogodą -->
      <div
        v-if="weatherData"
        class="flex-1 flex flex-col justify-center items-center p-6 rounded-lg shadow-md bg-white"
      >
        <img
          :src="`https://openweathermap.org/img/wn/${weatherData.weather[0].icon}.png`"
          alt="Aktualna pogoda"
          class="mx-auto mb-4"
        />
        <h2 class="text-2xl font-semibold text-gray-800 mb-4">
          Pogoda dla Krakowa
        </h2>
        <p class="text-lg text-gray-700 mb-2">
          Temperatura:
          <span class="font-medium">{{ weatherData.main.temp }}°C</span>
        </p>
        <p class="text-lg text-gray-700">
          Stan:
          <span class="font-medium">{{ weatherData.weather[0].main }}</span>
        </p>
      </div>

      <!-- Komunikat o ładowaniu -->
      <div v-else class="flex-1 text-center p-6 rounded-lg shadow-md bg-white">
        <p class="text-xl text-gray-800">Ładowanie danych o pogodzie...</p>
      </div>
      <!-- Prognoza na następne 5 dni -->
      <div
        v-if="forecastData"
        class="flex-1 text-center p-6 rounded-lg shadow-md bg-white"
      >
        <ul class="list-none space-y-2">
          <li
            v-for="(day, index) in forecast"
            :key="index"
            class="text-gray-700 flex items-center"
          >
            <img
              :src="`https://openweathermap.org/img/wn/${day.weatherIcon}.png`"
              alt="Pogoda"
              class="w-10 h-10 mr-2"
            />
            <span class="font-medium">{{ day.date }}: </span>
            {{ day.avgTemp }}°C - {{ day.weather }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      weatherData: null,
      forecastData: null,
    };
  },
  computed: {
    forecast() {
      if (!this.forecastData) return [];

      // Grupowanie danych pogodowych według daty
      const groupedForecast = this.forecastData.list.reduce(
        (result, forecast) => {
          const date = forecast.dt_txt.split(" ")[0];
          if (!result[date]) {
            result[date] = [];
          }
          result[date].push(forecast);
          return result;
        },
        {}
      );

      // Obliczanie średniej temperatury dla każdego dnia
      const avgForecast = Object.entries(groupedForecast).map(
        ([date, forecasts]) => {
          const avgTemp =
            forecasts.reduce((sum, forecast) => sum + forecast.main.temp, 0) /
            forecasts.length;
          return {
            date,
            avgTemp: avgTemp.toFixed(1),
            weather: forecasts[0].weather[0].main,
            weatherIcon: forecasts[0].weather[0].icon,
          };
        }
      );

      return avgForecast;
    },
  },
  methods: {
    async fetchWeatherData() {
      const apiKey = "f8ceac7f72550e6bfbdfb48412aa7f94";
      const weatherUrl = `https://api.openweathermap.org/data/2.5/weather?q=Krakow,pl&appid=${apiKey}&units=metric&lang=pl`;
      const forecastUrl = `https://api.openweathermap.org/data/2.5/forecast?q=Krakow,pl&appid=${apiKey}&units=metric&lang=pl`;

      try {
        const weatherResponse = await axios.get(weatherUrl);
        const forecastResponse = await axios.get(forecastUrl);

        this.weatherData = weatherResponse.data;
        this.forecastData = forecastResponse.data;
      } catch (error) {
        console.error("Błąd podczas pobierania danych: ", error);
      }
    },
  },
  mounted() {
    this.fetchWeatherData();
  },
};
</script>
