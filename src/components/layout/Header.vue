<template>
<header class="header">
     <div class="nav-box">
         <h1>TodoList</h1>
          <div id="nav">
            <router-link to='/'>Home</router-link>|
            <router-link to='/about'>About</router-link>
          </div>
     </div>
    
    
     
</header>
</template>

<script>
export default {
    name:"Header"
}
</script>


<style scoped>
.header {
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
    width: 50%;
    margin: auto;
}
.header a {
    color: #fff;
    padding-right:5px ;
    text-decoration: none;
}
.nav-box {
    position: relative;
}

</style>