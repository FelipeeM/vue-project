<template>
    <div id ="nav">     
        <h3 id ="titulo">Interface Vue com CRUD</h3>
    </div>
    <div class="fixed-action-btn">
      <router-link to="edit-user" class="btn-floating btn-large blue">
        <i class="fa fa-pencil"></i>
      </router-link>
      <router-link to="add-user" class="btn-floating btn-large blue">
        <i class="fa fa-plus" ></i>
      </router-link>
      <router-link to="/" class="btn-floating btn-large blue">
        <i class="fa fa-list" ></i>
      </router-link>
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
    background-color: rgb(66, 140, 224);
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    
}
#button-nav{
    justify-content: right;

}
#titulo{
    color: rgb(255, 255, 255);
    justify-content: center;
}
</style>