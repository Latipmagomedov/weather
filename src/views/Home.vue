<template>
  <section class="home">
    <div class="container">
      <div class="home__description">
        <h1 class="home__title">Узнать погоду</h1>
        <p class="home__subtitle">
          Чтобы узнать свою погоду, найдите свой город
        </p>
      </div>

      <form
        @submit.prevent="
          $router.push({ path: '/search-result', query: { city: search } })
        "
        class="home__search"
      >
        <input
          type="text"
          class="home__search-inp"
          placeholder="Поиск городов"
          v-model="search"
        />
        <button type="submit" class="home__search-btn"></button>
      </form>

      <div class="home__cities">
        <h2 class="home__cities-title">Города</h2>

        <div class="home__cities-slider">
          <splide :options="options">
            <splide-slide v-for="(city, index) in cities" :key="index">
              <router-link
                :to="{ path: '/search-result', query: { city: city } }"
              >
                <div class="home__cities-slide">
                  <div class="home__cities-filter">
                    <h3 class="home__cities-name">{{ city }}</h3>
                  </div>
                </div>
              </router-link>
            </splide-slide>
          </splide>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { Splide, SplideSlide } from "@splidejs/vue-splide";

import "@splidejs/splide/dist/css/themes/splide-default.min.css";

export default {
  components: {
    Splide,
    SplideSlide,
  },
  data() {
    return {
      search: "",
      options: {
        rewind: true,
        perPage: 2,
        gap: "10px",
      },
      cities: [
        "Махачкала",
        "Дербент",
        "Москва",
        "Грозный",
        "Хасавюрт",
        "Кизляр",
        "Кизилюрт",
      ],
    };
  },
};
</script>

<style lang="scss">
.home {
  height: 100vh;
  min-height: 600px;
  display: flex;
  align-items: center;
  padding-bottom: 15px;
  background-image: url(https://images.unsplash.com/photo-1496568816309-51d7c20e3b21?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1189&q=80);
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

.home__description {
  max-width: 300px;

  .home__subtitle {
    max-width: 260px;
    margin-top: 5px;
    color: #ffffffe5;
    font-size: 14px;
  }
}

.home__search {
  width: 100%;
  margin-top: 40px;
  border-radius: 13px;
  display: flex;
  align-items: center;
  background-color: #ffffff38;

  input {
    width: 85%;
    background-color: transparent;
    color: rgb(255, 255, 255);
    font-weight: 600;

    &::placeholder {
      color: #ffffffcb;
      font-weight: 600;
    }
  }

  button {
    width: 15%;
    min-width: 50px;
    background-color: transparent;
    background-image: url(../assets/icons/search.svg);
    background-size: 30%;
    background-position: center;
    background-repeat: no-repeat;
    cursor: pointer;
  }
}

.home__cities {
  margin-top: 30px;

  .home__cities-slider {
    margin-top: 20px;

    .splide__list {
      .splide__slide {
        a {
          text-decoration: none;
        }
        .home__cities-slide {
          position: relative;
          width: 100%;
          height: 300px;
          border-radius: 13px;
          background-image: url(../assets/image/cities/1.jpg);
          background-size: cover;
          background-position: center;
          background-repeat: no-repeat;
          overflow: hidden;

          .home__cities-filter {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: #0000003b;
          }

          .home__cities-name {
            position: absolute;
            top: 80%;
            left: 10%;
            color: #fff;
            text-decoration: none;
          }
        }
      }

      .splide__slide:nth-child(1n + 1) {
        .home__cities-slide {
          background-image: url(../assets/image/cities/1.jpg);
        }
      }
      .splide__slide:nth-child(2n + 2) {
        .home__cities-slide {
          background-image: url(../assets/image/cities/2.jpg);
        }
      }
      .splide__slide:nth-child(3n + 3) {
        .home__cities-slide {
          background-image: url(../assets/image/cities/3.jpg);
        }
      }
    }

    .splide__pagination {
      margin-bottom: -50px;
    }
  }
}
</style>