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
body {
  font-family: tahoma;
  color: #282828;
  margin: 0px;
}

.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 15px;
}

.product {
  display: flex;
}

img {
  border: 1px solid #d8d8d8;
  width: 70%;
  margin: 40px;
  box-shadow: 0px 0.5px 1px #d8d8d8;
}

.product-image {
  flex-basis: 700px;
}

.product-info {
  margin-top: 10px;
  flex-basis: 500px;
}

.color-box {
  width: 40px;
  height: 40px;
  margin-top: 5px;
}

.cart {
  margin-right: 25px;
  float: right;
  border: 1px solid #d8d8d8;
  padding: 5px 20px;
}

button {
  margin-top: 30px;
  border: none;
  background-color: #1e95ea;
  color: white;
  height: 40px;
  width: 100px;
  font-size: 14px;
}

.disabledButton {
  background-color: #d8d8d8;
}

.review-form {
  width: 30%;
  padding: 20px;
  border: 1px solid #d8d8d8;
}

input {
  width: 100%;
  height: 25px;
  margin-bottom: 20px;
}

textarea {
  width: 100%;
  height: 60px;
}
</style>
