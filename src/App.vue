<template>
  <div id="app">
    <div id="nav">
      <div class="alert alert-danger" role="alert">
  Seus melhores produtos com comentários!
</div> <br>

      <!--<router-link to="/">Home</router-link> -->
     <!-- <router-link to="/about">About</router-link><br>-->
      <!-- <router-link to="/Cadastro">Cadastro</router-link><br>-->
      <router-link to="/Produtos">Produtos</router-link> <br><br>
      <router-link to="/Comentario">Comentario</router-link> <br><br> 
              
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #090611;
}

#nav {
  padding: 10px;
 
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #b94256;
}
</style>
