<template>
  <div class="main-container">
    <Marquee />
    <router-view/>

  </div>
  
</template>

<script>
import Marquee from "./components/Marquee.vue";
  export default{
    components:{
      Marquee
    }
  }

</script>

<style>
*{
  font-family: 'Open Sans', sans-serif, Arial;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.table-coins-container{
  min-height: 700px;
  width: 100vw;
  padding: 35px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>
