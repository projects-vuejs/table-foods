<template>
<div>
  <h1 :style="{ color }">Minha Lista</h1>
  <input 
    id="input"
    @keyup.enter="addFood"
    type="text" 
    v-model="currentFood">
  <button @click="addFood">
    Add!
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
    color: "#79C7C5",
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
    }
  }
}
</script>
<style>
body{
  text-align: center;
  background-color:#ADE1E5;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
h1{
  text-shadow: 1px 1px black;
  padding: 5px;
  font-size: 50px;
}
input{
  width: 200px;
  height: 30px;

  margin: 2px;
  text-align: center;

  border-radius: 5px;
  border: 2px solid #000501;

  background-color: #0005017a;
}
input:focus{
  transition-duration: 2s;
  background-color: #00050142;
}
button{
  width: 200px;
  height: 36px;

  margin: 2px;
  border-radius: 5px;

  color: #ADE1E5;
  background: #0005017a;
}
div{
  background-color: #0005012a;
  height: 700px;
  border-radius: 5px;
}
ul{
  background-color: #0005017a;
  margin: 100px 50px;
}
ul li:nth-child(n){
  list-style: none;
  padding: 20px;
  margin: 20px 20px 20px 0;
  border-bottom: 1px solid #00050159;
}
ul li:last-child{
  list-style: none;
  padding: 20px;
  margin: 20px 20px 20px 0;
  border-bottom: none;
}
</style>