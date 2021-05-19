<template>
  <section class="home">
    <div class="container">
      <div class="home__description">
        <h1 class="home__title">Узнать погоду</h1>
        <p class="home__subtitle">
          Чтобы узнать свою погоду, найдите свой город
        </p>
      </div>

      <form class="home__search">
        <input
          type="text"
          class="home__search-inp"
          placeholder="Поиск городов"
        />
        <button type="submit" class="home__search-btn"></button>
      </form>

      <div class="home__cities">
        <h2 class="home__cities-title">Города</h2>

        <div class="home__cities-slider"></div>
      </div>
    </div>
  </section>
</template>

<script>
export default {};
</script>

<style lang="scss">
.home__description {
  max-width: 300px;
  margin-top: 80px;

  .home__subtitle {
    margin-top: 5px;
    color: #ffffffe5;
    font-size: 15px;
  }
}

.home__search {
  width: 100%;
  margin-top: 40px;
  border-radius: 13px;
  display: flex;
  align-items: center;
  background-color: #131313;

  input {
    width: 85%;
    background-color: transparent;
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
}
</style>