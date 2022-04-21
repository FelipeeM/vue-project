<template>
    <div id ="nav">     
            <h2 id ="titulo">Interface Vue com CRUD</h2>
        <div id ="button-nav"> 
            <router-link  to="/">Home</router-link> |
            <router-link  to="/about">About</router-link> |

            <router-link  to="/add-user">Adicionar usuario</router-link>
        </div>
    </div>
     <router-view/>
</template>
<script>


export default {
    name:"Navebar"
}
</script>

<style scoped>
#nav{
    background-color: rgb(241, 110, 110);
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: left;
    align-items: center;
    
}
#button-nav{
    justify-content: right;

}
#titulo{
    color: rgb(255, 255, 255);
    justify-content: left;
}
</style>