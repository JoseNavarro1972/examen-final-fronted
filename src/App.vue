<template>
  <div id="app">
    <nav>
      <router-link to="/calculo">Cálculo de calificaciones</router-link> |
      <router-link to="/formulario">Formulario de registro</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App'
};
</script>

<style scoped>
nav {
  margin-bottom: 20px;
  background-color: #17a2b8 !important;
    padding-top: .3125rem;
    padding-bottom: .3125rem;
    margin-right: 1rem;
    font-size: 1.25rem;
    line-height: inherit;
    white-space: nowrap;
    color: #fff;
}

nav a {
  margin-right: 10px;
  text-decoration: none;
  color: #fff;
}

nav a:hover {
  text-decoration: underline;
}
</style>


