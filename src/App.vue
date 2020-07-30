<template>
  <div id="app">
    <nav class="nav nav-pills flex-column flex-sm-row mb-4">
      <a class="flex-sm-fill text-sm-center nav-link active-class" aria-current="page" href="/">Home</a>
      <a class="flex-sm-fill text-sm-center nav-link" aria-current="page" href="/about">About</a>
    </nav>
    <main>
      <router-view />
    </main>
    <footer>this is a footer</footer>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Alegreya+Sans:wght@900&display=swap");
html {
  height: 100%;
  width: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #3b6978;
  background-color: #e4e3e3;
}
a.nav-link {
  background-color: #3b6978;
  color: #e4e3e3;
}

a.nav-link:hover {
  background-color: #84a9ac;
  color: #e4e3e3;
}
a.nav-link:active {
  background-color: #204051;
  color: #e4e3e3;
}

.btn-info {
  background-color: #204051;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-info:hover {
  background-color: #3b6978;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-info:focus {
  background-color: #84a9ac;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-primary {
  background-color: #84a9ac;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-primary:hover {
  background-color: #204051;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-primary:focus {
  background-color: #3b6978;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-sm {
  background-color: #204051;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-sm:hover {
  background-color: #3b6978;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

.btn-sm:focus {
  background-color: #84a9ac;
  color: #e4e3e3;
  border-color: #e4e3e3;
}

h1.snackshack {
  font-family: "Alegreya Sans", sans-serif;
}

li.errors {
  color: red;
  list-style: none;
  margin-right: 2rem;
}

img {
  width: 20em;
}
</style>
