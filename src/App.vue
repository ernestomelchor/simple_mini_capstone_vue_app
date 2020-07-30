<template>
  <div id="app">
    <nav class="nav nav-pills flex-column flex-sm-row mb-4">
      <a class="flex-sm-fill text-sm-center nav-link active-class" aria-current="page" href="/">Home</a>
      <a class="flex-sm-fill text-sm-center nav-link" aria-current="page" href="/about">About</a>
    </nav>
    <main>
      <router-view />
    </main>
    <footer>SnackShack &#169; 2020</footer>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Alegreya+Sans:wght@900&display=swap");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
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

footer {
  background-color: #3b6978;
  color: #e4e3e3;
  min-height: 10vh;
  padding-top: 4vh;
  border-width: 10px;
  border-top-color: red;
}
h1.snackshack {
  font-family: "Alegreya Sans", sans-serif;
}

li.errors {
  color: red;
  list-style: none;
  margin-right: 2rem;
}

main {
  min-height: 100vh;
}

img {
  width: 20em;
}
</style>
