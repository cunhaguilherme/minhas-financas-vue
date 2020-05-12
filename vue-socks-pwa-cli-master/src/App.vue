<template>
  <div id="app">
    <div class="product-logo">
      <center><img src= "https://i.dlpng.com/static/png/6695128_preview.png" height=120></center>
    </div>
    
    <div class="product-info">
      <h1>{{ titulo }}</h1>
    </div>

    <div class="areaBotoes">
      <button v-on:click="importar">Importar</button>
      <button v-on:click="apagar">Apagar</button>
    </div>
    <financa @financa-submitted="addFinanca"></financa>
    <div class="tabela-retorno">
      <table>
        <tr>
          <th>Item</th>
          <th>Data</th>
          <th>#</th>
          <th>$</th>
        </tr>
        <tr v-for="financa in financaRetorno"
        :key="financa.item">
          <td>{{financa.item}}</td>
          <td>{{financa.data}}</td>
          <td>{{financa.quantidade}}</td>
          <td>{{financa.valor}}</td>        
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import Financa from "./components/Financa.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    financa: Financa
  },
  data() {
    return {
        financaRetorno: [],
        titulo: "Minhas Finanças"
    };
  },
  methods: {
    addFinanca(financa) {
      console.log("Passou pelo push");
      console.log(financa.item);
      this.financaRetorno.push(financa);
      console.log(this.financaRetorno[0].quantidade);
    },
    apagar(){
      this.financaRetorno = [];
    },
    importar(){
      axios
        .get("https://evening-badlands-20922.herokuapp.com/financas/semana")
        .then(response => {
          response.data.map(item => this.financaRetorno.push(item));
          //this.financaRetornoresponse.data;
          //console.log(response.data);
        })
        .catch(e => {
          console.log(e);
        })
    }
  }
};
</script>

<style scoped>
.product-info{
    text-align: center!important;
}

.areaBotoes{
    text-align: center;
}


.text-center {
    text-align: center!important;
}

body{
  margin: 0;
    font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Noto Color Emoji";
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    color: #212529;
    text-align: left;
    background-color: #fff;
    padding-left: 8px;
    padding-right: 8px;
}
label{
    display: inline-block;
    margin-bottom: .5rem;
}
input{display: block;
    width: 95%;
    height: calc(1.5em + .75rem + 2px);
    padding: .375rem .75rem;
    font-size: 1rem;
    font-weight: 400;
    line-height: 1.5;
    color: #495057;
    background-color: #fff;
    background-clip: padding-box;
    border: 1px solid #ced4da;
    border-radius: .25rem;
    transition: border-color .15s ease-in-out,box-shadow .15s ease-in-out;
}
button {
    color: #fff;
    background-color: #007bff;
    border-color: #007bff;
    border-radius: 5px;
    padding: 8px 20px 8px 20px;
    font-size: 17px;
    margin: 10px;
}

table {
  font-family: 'Open Sans', sans-serif;
  width: 100%;
  border-collapse: collapse;
  padding-left: 8px;
  padding-right: 8px;
}

table th {
  font-weight: bold;
  text-align: left;
  background: #FFFFFF;
  border-top: 1px solid #A9A9A9;
  border-bottom: 1px solid #A9A9A9;
  padding-left: 8px;
  padding-right: 8px;
  min-width: 30px;
}

table td {
  font-weight: normal;
  text-align: left;
  padding-left: 8px;
  padding-right: 8px;
  border-top: 1px solid #A9A9A9;
  border-bottom: 1px solid #A9A9A9;
}
</style>
