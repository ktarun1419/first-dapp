<template>
  <div id="app">
    <div id="nav">
      <h1 class="name">DIVINE ANARCHY</h1>
      <!-- <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link> -->
      <md-tabs class="md-transparent" md-alignment="fixed">
      <md-tab id="tab-home" md-label="Home" to="/"></md-tab>
      <md-tab id="tab-pages" md-label="Roadmap" to="/eerr"></md-tab>
      <md-tab id="tab-posts" md-label="Game theory" to="/about"></md-tab>
      <md-tab id="tab-favorites" md-label="Team" to="/ee"></md-tab>
      <md-tab id="tab-favorites" md-label="Faq" to="/eee"></md-tab>
    </md-tabs>
    <router-view/>
    </div>
    
    <link rel="stylesheet" href="//fonts.googleapis.com/css?family=Roboto:400,500,700,400italic|Material+Icons">
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  font-size: 120%;
  background-color: black;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: white;

    &.router-link-exact-active {
      color: #b94242;
    }
  }
}
.name{
  font-family: sans-serif ;
  font-size: 200%;
  text-align: left;
}
.md-tabs {
    margin-bottom: 24px;
  }
</style>
