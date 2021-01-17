<template>
  <div class="box_list">
    <ul>
        <li 
        v-for="(food, index) in foods"
        :key="`${food}-${index}`">{{ food }}</li>
    </ul>
  </div>
</template>

<script>
const MAX_FOODS = 5
export default {
    props: {
        foods: {
            type: Array, default: () => []
        }
    },
    watch: {
        foods () {
            if(this.foods.length === MAX_FOODS){
                this.$emit('stop', 'Sua cesta está cheia!!')
            }
            
        }
    }
}
</script>

<style>

</style>