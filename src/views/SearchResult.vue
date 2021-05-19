<template>
  <section class="result" v-if="weather.cod == 200">
    <div class="container">
      <div class="result__back" @click="$router.push('/')">
        <img src="@/assets/icons/arrow.svg" alt="back" />
        <p>Назад</p>
      </div>
      <div class="result__content">
        <h2 class="result__content-city">{{ city }}</h2>
        <div class="result__content-status">
          <p class="result__content-temp">{{ temp }} &deg;</p>
        </div>
        <img class="result__content-icon" :src="icon" alt="icon" />
        <p class="result__content-desc">{{ description }}</p>
        <p class="result__content-wind">Скорость ветра в сек: {{ speed }}</p>
      </div>
    </div>
  </section>
  <section class="result error" v-else>
    <div class="container">
      <div class="result__back" @click="$router.push('/')">
        <img src="@/assets/icons/arrow.svg" alt="back" />
        <p>Назад</p>
      </div>
      <div class="result__content">
        <h2 class="result__content-city">Город не найден</h2>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      city: this.$route.query.city,
      weather: "",
      icon: ``,
      temp: "",
      description: "",
      speed: "",
    };
  },
  created: function () {
    console.log(this.city);
    fetch(
      `https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=839f5941957cea63b64cfc3b53623e66`
    )
      .then((resp) => resp.json())
      .then((res) => {
        this.weather = res;
        this.icon = `https://openweathermap.org/img/wn/${this.weather.weather[0].icon}@2x.png`;
        this.temp = this.weather.main.temp;
        this.description = this.weather.weather[0].description;
        this.speed = this.weather.wind.speed;
        console.log(res);
      });
  },
};
</script>

<style lang="scss" scope>
.result {
  width: 100%;
  height: 100%;
  min-height: 600px;
  background-image: url(https://images.unsplash.com/photo-1496568816309-51d7c20e3b21?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1189&q=80);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  .container {
    position: relative;
    height: 100vh;
    min-height: 600px;
    display: flex;
    align-items: center;
  }
}

.result__back {
  top: 20px;
  left: 0px;
  position: absolute;
  display: flex;
  align-items: center;
  p {
    margin-left: 10px;
    color: #1771f1;
  }
}
.result__content {
  width: 100%;
  padding: 30px 15px;
  border-radius: 13px;
  background-color: #0000008e;
  display: flex;
  flex-direction: column;
  align-items: center;

  .result__content-city {
    font-size: 25px;
  }

  .result__content-status {
    margin-top: 15px;
    display: flex;
    align-items: center;

    p {
      font-size: 33px;
      font-weight: 900;
    }
  }

  img.result__content-icon {
    max-width: 60px;
    margin-top: 5px;
  }

  .result__content-desc {
    margin-top: -5px;
    font-size: 20px;
    font-weight: 600;
  }

  .result__content-wind {
    margin-top: 40px;
    font-size: 12px;
  }
}
</style>