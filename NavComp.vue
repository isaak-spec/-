<template>
<div class="container">
    <nav>
        <router-link to="/">Home page</router-link>
        <router-link to="/chat">Chat page</router-link>
        <router-link to="/test">Test API page</router-link>
    </nav>
</div>
</template>

<script>
export default {
    name: 'NavComp'
 
}
</script>


<style scoped>
.container{
    background-color: #f0f8;
    height: 70%;
    display: flex;
    justify-content: center;
}


nav{
    width: 450px;
    height: 150%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
}
</style>