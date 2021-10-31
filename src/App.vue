<template>
  <div id="app">
    <div id="nav">

      <div class="navbar">
        <h2 style="float:left; margin-left:40px; font-size:27px">DIVINE ANARCHY</h2>
  <a href="#home" style="float:left; margin-left:100px;color:white; font-size:18px;">Home</a>
  <a  href="#cvd" style="float:left;margin-left:20px; color:white;font-size:18px;">Roadmap</a>
  <a href="#contact" style="float:left;margin-left:20px;color:white;font-size:18px;">Game Theory</a>
  <a href="#contact" style="float:left;margin-left:20px;color:white;font-size:18px;">Team</a>
  <a href="#contact" style="float:left;margin-left:20px;color:white;font-size:18px;">FAQ</a>
  <button style="float:right;color:#b94242; font-size:18px;padding:10px 26px; background-color:white;margin-right:100px; margin-top:5px">Connected</button>
</div>
       <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <!-- <md-tabs class="md-transparent" md-alignment="fixed" style="position:fixed;">
      <md-tab id="tab-home" md-label="Home" to="/"></md-tab>
      <md-tab id="tab-pages" md-label="Roadmap" to="/roadmap"></md-tab>
      <md-tab id="tab-posts" md-label="Game theory" to="/about"></md-tab>
      <md-tab id="tab-favorites" md-label="Team" to="/team"></md-tab>
      <md-tab id="tab-favorites" md-label="Faq" to="/faq"></md-tab>
    </md-tabs> -->
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
  background-color: #17161b;
}
.navbar {
  overflow: hidden;
  background-color:#17161b;
  position: fixed; /* Set the navbar to fixed position */
  top: 0; /* Position the navbar at the top of the page */
  width: 100%; /* Full width */
  margin-bottom: 30px;
}

/* Links inside the navbar */
.navbar a {
  display: inline-block;
  display: block;
  color: #f2f2f2;
  padding: 14px 16px;
  text-decoration: none;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 15px;
}

/* Change background on mouse-over */
.navbar a:hover {
  background:#b94242;
  color:white;
}
.name{
  font-family: sans-serif ;
  font-size: 200%;
  text-align: left;
}

</style>
