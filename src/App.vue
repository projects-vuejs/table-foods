<template>
<div id="box">
  <input 
    id="input"
    @keyup.enter="addFood"
    type="text" 
    v-model="currentFood"
    placeholder="Coloque Aqui!">
  <button 
    @click="addFood">
    Adicionar
  </button>
  <button
    id="btn_reset"
    @click="reseta">
    Resetar
  </button><br>
  <food-list 
    @stop="handleStop"
    :foods="foods"/>
</div>
</template>

<script>
import FoodList from './components/foodList'

export default {
  components: { FoodList },
  data: () => ({
    currentFood: "",
    link: "http://www.g1.globo.com",
    foods: ['Maçã', 'Pera']
  }),
  methods: {
    handleStop (payload) {
      console.log("Payload => ", payload)
      alert(payload)
      document.getElementById("input").disabled = true
    },
    addFood () {
      this.foods.push(this.currentFood)
      this.currentFood = ''
    },
    reseta () {
      window.location.reload()
    }
  }
}
</script>
<style>
body{
  text-align: center;
  background-color:#fff;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
*{
  box-sizing: border-box;
}
#box{
  padding: 50px;
  text-align: center;
}
input{
  width: 200px;
  height: 50px;

  margin: 2px;
  text-align: center;

  border: none;
  border-bottom: 2px solid #FF9F1C;

  background-color: none;
  color: #FF9F1C;
  font-weight: 800;
}
input::placeholder{
  color: #FF9F1C;
}
input:focus{
  outline: none; /* Retira a borda quando focar */
  transition-duration: 2s;
}
button{
  width: 200px;
  height: 56px;

  margin: 2px;
  border: 1px solid #FF9F1C;
  border-radius: 10px;

  cursor: pointer;

  color: #FF9F1C;
  background: transparent;
  text-transform: uppercase;
  font-weight: 800;
}
button:focus{
  outline: none;
}
#btn_reset{
  color: rgb(255, 0, 0);
  border: 1px solid #ff0000;
}
.box_list{
  margin: 20px 20px 20px -15px;
}
ul{
  margin: 0 auto;
  width: 50%;
  text-align: left;
}
ul li:hover{
  background: #ecbc98;
  cursor: pointer;
}
ul li:nth-child(n){
  list-style: none;
  padding: 20px;
  color: #EE8434;
}
ul li:last-child{
  list-style: none;
  padding: 20px;
  border-bottom: none;
  color: #EE8434;
}
</style>