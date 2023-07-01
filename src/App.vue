<template>
  <div :class="{ 'dark-mode': isDarkMode }">
    <nav class="navbar navbar-expand-lg fixed-top"
      :class="{ 'navbar-dark bg-dark': isDarkMode, 'navbar-light bg-white': !isDarkMode }">
      <div class="container d-flex justify-content-between">
        <a class="navbar-brand" href="#">Stefano Di Sanza</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
          aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse justify-content-end" id="navbarNav">
          <ul class="navbar-nav ml-auto align-items-center">
            <li class="nav-item">
              <router-link class="nav-link" :class="{ 'text-black': !isDarkMode }" to="/">Home</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" :class="{ 'text-black': !isDarkMode }" to="/about">Chi sono</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" :class="{ 'text-black': !isDarkMode }" to="/portfolio">Portfolio</router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link" :class="{ 'text-black': !isDarkMode }" to="/contacts">Contatti</router-link>
            </li>
            <li>
              <!-- Switch per la dark mode -->
              <div class="form-check form-switch ms-5">
                <input class="form-check-input" type="checkbox" id="dark-mode-switch" v-model="isDarkMode">
                <label class="form-check-label p" for="dark-mode-switch">
                  <font-awesome-icon :icon="isDarkMode ? 'sun' : 'moon'" />
                </label>
              </div>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<script>
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faMoon, faSun } from '@fortawesome/free-solid-svg-icons'

library.add(faMoon, faSun)

export default {
  components: {
    FontAwesomeIcon
  },
  data() {
    return {
      isDarkMode: false
    }
  },
  mounted() {
    this.$watch('isDarkMode', (newVal) => {
      if (newVal) {
        document.body.classList.add('bg-dark');
        document.body.classList.add('text-light');
      } else {
        document.body.classList.remove('bg-dark');
        document.body.classList.remove('text-light');
      }
    });
  }
}
</script>

<style scoped>
.dark-mode .navbar {
  background-color: #333;
  color: #f2f2f2;
}

.navbar-light.bg-white {
  background-color: #fff;
}

.navbar-nav .nav-link.text-black {
  color: #000;
}
</style>
