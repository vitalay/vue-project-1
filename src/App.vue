

<script >

export default {

  data() {
    return {
      city: ""
    }
  }

}

</script>

<template>
  
  <div class="wrapper">
  <h1>Погодное приложение </h1>
  <p>Узнать погоду в  {{ city ==  "" ? "вашем городе" : city}}</p>
  <input type="text" v-model="city" placeholder="Введите город">
  <button>Получить погоду</button>
  </div>

</template>






<style scoped>
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
