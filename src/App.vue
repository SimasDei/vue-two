<template>
  <div id="app">
    <div id="nav">
      <router-link class="btn" to="/">Home</router-link>
      <router-link class="btn" to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
html {
  background: #333;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.todo__section {
  max-width: 80%;
  margin: auto;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
  text-decoration: none;
}
.btn:hover,
.btn:active {
  background: #666;
}
</style>
