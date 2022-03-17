<template>
    <header id="app-header">
        <div id="marquee-container">
            <h1>Real Time Crypto Marketcap</h1>
        </div>
        <div id="navbar">
            <router-link to="/">HOME</router-link>
            <router-link to="/about">ABOUT</router-link>

        </div>
    </header>
</template>

<script>
    export default{
        name: "Marquee"
    }
</script>

<style scoped>
 #app-header{
     width: 100 vw;
     height: 100px;
     background-color: #222;
     color: #fff;
     display: flex;
     flex-direction: column;
     justify-content: center;
     align-items: center;
 }
 #navbar a{
     color: #fff;
     text-decoration: none;
     padding: 5px;

 }
</style>