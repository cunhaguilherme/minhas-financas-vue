<template>
  <div class="financa">
    <form class="review-form" @submit.prevent="onSubmit">
      <p>
        <label for="item">Item:</label>
        <input id="item" v-model="item" placeholder="item">
      </p>
      <p>
        <label for="data">Data:</label>
        <input type="date" id="data" v-model="data" placeholder="data">
      </p>
      <p>
        <label for="quantidade">Quantidade:</label>
        <input type="number" id="quantidade" v-model="quantidade" placeholder="quantidade">
      </p>
      <p>
        <label for="valor">Valor:</label>
        <input id="valor" v-model="valor" placeholder="valor">
      </p>
      <p>
        <input type="submit" value="Submit">  
      </p>
    </form>
  </div>
</template>

<script>
export default {
  name: "Financa",
  data(){
    return {
      item: null,
      data: null,
      quantidade: null,
      valor: null
    }
  },
  methods: {
    onSubmit() {
      console.log("passou pelo submit");
      let financa = {
        itemId: 1 + this.quantidade * this.valor,
        item: this.item,
        data: this.data,
        quantidade: this.quantidade,
        valor: this.valor
      }
      this.$emit('financa-submitted', financa)
      this.itemId = null,
      this.item = null,
      this.data = null,
      this.quantidade = null,
      this.valor = null      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.product-info{
    text-align: center!important;
}

.areaBotoes{
    text-align: center;
}

button{
    margin: 10px;
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
