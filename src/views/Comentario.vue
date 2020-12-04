<template>
  <div class="row">
    <div class="col-4">
      <div class="card-deck">
        <div class="card" style="">
          <div class="card-is-two-thirds">
            <img
              :src="produto.urlImagem"
              class="img-fluid img-thumbnail"
              alt=""
            />

            <h5 class="card-title">{{ produto.nome }}</h5>
            <p class="card-text">Valor: {{ produto.preco }}</p>
            <p class="card-text">Peso: {{ produto.peso }}gr</p>
          </div>
        </div>
      </div>
    </div>
    <div class="col-4">
      <div class="form-group">
        <label for="exampleFormControlTextarea1"></label>
        <textarea
          v-model="comentario.comentario"
          class="form-control"
          id="exampleFormControlTextarea1"
          rows="3"
        ></textarea>
      </div>
      <button @click="salvar()" class="btn btn-primary">
        Salvar Comentário
      </button>
    </div>
    <div class="col-4">
      <ul class="list-group">
        <li v-for="item in comentarios" :key="item.id" class="list-group-item">
          {{item.comentario}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      //rota deste, pegar parametro id
      id: this.$route.params.id,
      produto: { id: this.id, nome: "", preco: 0, peso: 0, urlimagem: "" },
      comentario: { produtoId: this.id, comentario: "" },
      comentarios: [],
    };
  },
  methods: {
    salvar() {      
      axios
        .post("https://localhost:5001/Comentario", {
          produtoId:Number( this.id),
          comentario: this.comentario.comentario,
        })
        .then(() => {
          this.start();
        });
    },
    start() {
      axios
        .get("https://localhost:5001/Produto/" + this.id)
        .then((resposta) => {
          console.log(resposta);
          this.produto = resposta.data;
        });
      axios
        .get("https://localhost:5001/Comentario/" + this.id)
        .then((resposta) => {
          console.log(resposta);
          this.comentarios = resposta.data;
        });
    },
  },
  mounted() {
    this.start();
  },
};
</script>

<style>
</style>