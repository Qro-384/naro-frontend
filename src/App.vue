<template>
  <main>
    <div :class="$style.container">
      <header :class="$style.header">
        <router-link to="/">Home</router-link>
        |
        <router-link to="/ping">Ping</router-link>
        |
        <router-link to="/login">Login</router-link>
        |
        <router-link :to="{name: 'city', params:{ cityName: 'Tokyo' }}">Tokyo</router-link>
        |
        <router-link to="/countries">countries</router-link>
        |
        <router-link :to="{name: 'country', params:{ countryName: 'Japan' }}">Japan</router-link>
        |
        <router-link to="/test">Test</router-link>
      </header>

      <router-view />
    </div>
  </main>
</template>

<style module>
.container {
  max-width: fit-content;
  margin: auto;
}
.header {
  display: flex;
  justify-content: center;
}
</style>