<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark primary-color fixed-top">
      <a class="navbar-brand" style="color:white">Vue.js</a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#basicExampleNav"
        aria-controls="basicExampleNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="basicExampleNav">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <router-link class="nav-link" :to="{name: 'HelloWorld'}">Utilisateurs</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" :to="{name: 'About'}">A propos</router-link>
          </li>
        </ul>
      </div>
    </nav>
    <div style="margin-top: 5em">
      <router-view/>
    </div>
  </div>
</template>

<script>
export default {}
</script>
