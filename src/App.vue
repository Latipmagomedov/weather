<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500;600;700;800;900&display=swap');

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  outline: none;
}

body {
  background-color: #0a0a0a;
  color: #ffff;
  font-family: 'Montserrat', sans-serif;
}

.container {
  width: 93%;
  max-width: 480px;
  margin: 0 auto;
}

button, input {
  height: 50px;
  background-color: #ffffff0e;
  border-radius: 10px;
  border: none;
  font-family: 'Montserrat', sans-serif;
}

button {
  padding: 0 13px;
}

input {
  padding-left: 15px;
  color: #fff;
}

h1 {
  font-size: 38px;
}

h2 {
  font-size: 25px;
}

a {
  color: #1771F1;
}
</style>
