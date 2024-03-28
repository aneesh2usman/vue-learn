<script setup>
import {ref} from "vue"
const count = ref(0);
const  addCount = ()=>{
  count.value =  count.value +1
}
const removeCount = () =>{
  count.value =  count.value -1
}
</script>
<!-- <script >
export default {
  data() {
    return {
      count:0
    }
  },
  methods: {
    addCount(){
      this.count =  this.count+1
    },
    removeCount(){
      this.count =  this.count-1
    }
  }
  
}
</script> -->

<template>
  <main>
    <div>
      <h4 class="mb-4"> Aneesh</h4>
    <h1>{{ count }}</h1>
    <button @click="addCount()">+</button>
    <button  @click="removeCount()">-</button>
    </div>
  </main>
</template>
<style>
main {
  background-color: aliceblue;
  height: 100vh;
  width: 100vh;
  align-items: center;
  justify-content: center;
}
div{
  text-align: center;
}
</style>