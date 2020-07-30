<template>
  <div id="app">
    <nav class="nav nav-pills flex-column flex-sm-row mb-4">
      <a class="flex-sm-fill text-sm-center nav-link active-class" aria-current="page" href="/">Home</a>
      <a class="flex-sm-fill text-sm-center nav-link" aria-current="page" href="/about">About</a>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  margin-top: 0 auto;
  margin-left: 0 auto;
  margin-right: 0 auto;
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

li.errors {
  color: red;
  list-style: none;
  margin-right: 2rem;
}

img {
  width: 20em;
}
</style>
