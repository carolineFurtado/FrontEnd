<template>
  <div class="row">
    <div class="col-4" v-for="produto in produtos" :key="produto">
      <div class="card-deck">
        <div class="card" style="">
          <div class="card-is-two-thirds">
  
  <div class="col-4"></div>
    <img :src="produto.urlImagem" class="img-fluid img-thumbnail" alt="" width="400" height="210"/>

            <h5 class="card-title">{{ produto.nome }}</h5>
            <p class="card-text">Valor: {{ produto.preco }}</p>
            <p class="card-text">Peso: {{ produto.peso }}gr</p>
    
    
   
    <router-link
              class="btn btn-success" @click="salvar()"  
              :to="{ path: '/Comentario/' + produto.id }">Comentar</router-link>
    </div> 
     </div> 
      </div>            
  </div>  
  </div> 
</template>

<script>
import axios from "axios";
export default {    
    data(){
      return {
        produtos: [],
        nome:"",
        preco:"",
        peso:"",
        urlImagem:"",  
    };
  }, 
    methods: {
      salvar(){
         axios.post("https://localhost:5001/Produto",{
           nome:this.nome, 
           preco:this.preco,
           peso:this.peso, 
           urlImagem:this.urlImagem})
           .then(() =>{
             this.start(); 
        });
      },
      start(){
          axios.get("https://localhost:5001/Produto").then(resposta =>{
          console.log(resposta);
          this.produtos = resposta.data;
        });
    }, 

      
    },
    mounted(){
      this.start();
    }
  };  
  
  

</script>

<style>
</style>
