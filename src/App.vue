<script>
import axios from 'axios'

export default {

  data() {
    return {
      city: "",
      error: "",
      info: null
    }
  },
  computed: {
    cityName() {
      return "<<" + this.city + ">>"
    },
    showTemp() {
      return "Температура: " + this.info.main.temp 
    },
    showFeelsLike() {
      return "Ощущается как: " + this.info.main.feels_like
    },
    showMinTemp() {
      return "Минимальная: " + this.info.main.temp_min
    },
    showMaxTemp() {
      return "Максимальная: " + this.info.main.temp_max
    }
    
  },
  methods: {
    getWeather() {
      if (this.city.trim().length < 2) {
        this.error = "Название города должно быть больше 1 символов :)"
        return false

      }
       this.error = ""
       https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=2ad553dea87107e590ed7de670b4a4d8
       axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=2ad553dea87107e590ed7de670b4a4d8
`)   
            .then(res => (this.info = res.data))
    }

  }
  

}
</script>

<template>
  <div class="wrapper">
    <h1>Погодное приложение</h1>
    <p>Узнать погоду в {{ city == "" ? "вашем городе" : cityName }}</p>
    <input type="text" v-model="city" placeholder="Введите город" />
    <button v-if="city != ''" @click="getWeather()">Получить погоду</button>
    <button disabled v-else>Введите название города</button>
    <p class="error"> {{ error }} </p>

    <div v-if="info != null">
          <p>{{ showTemp }}</p>
          <p>{{ showFeelsLike }}</p>
          <p>{{ showMinTemp }}</p>
          <p>{{ showMaxTemp }}</p>
    </div>
    
  </div>
</template>

<style scoped>
.error {
  color: #d03939;
}

.wrapper {
  width: 900px;
  height: 500px;
  border-radius: 50px;
  padding: 20px;
  background: #1f0f24;
  text-align: center;
  color: #fff;
}
.wrapper h1 {
  margin-top: 50px;
}
.wrapper p {
  margin-top: 20px;
}
.wrapper input {
  margin-top: 35px;
  background: transparent;
  border: 0;
  border-bottom: 2px solid #110813;
  color: #fcfcfc;
  padding: 8px 15px;
  font-size: 18px;
  outline: none;
}
.wrapper input:focus {
  border-bottom: 2px solid #e912d7;
}

.wrapper button:disabled {
  background: #746027;
  cursor: not-allowed;
}

.wrapper button {
  background: #2ab69e;
  color: #fff;
  border-radius: 10px;
  border: 2px solid #b99935;
  padding: 10px 15px;
  margin-left: 20px;
  cursor: pointer;
  transition: transform 500ms ease;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
</style>
