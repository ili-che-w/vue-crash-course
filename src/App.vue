<template>
  <div id="app">
    <header class="container-fluid">
      <h1>Todo application</h1>
    </header>

    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  width: 40%;
  max-width: 800px;
  margin: 0 auto;
}

.container-fluid {
  width: 100%;
}

.row {
  display: flex;
  justify-content: space-between;
  margin-bottom: 2rem;
}
</style>
