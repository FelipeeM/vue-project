<template>
  <div id="view-employee">
    <h3>Usuários</h3>
    <ul clas="collection with-header">
      <li class="collection-header"><h5>Nome  | Idade  | Regiao  | Id</h5></li>
    </ul>  
    <ul v-for="user in users" v-bind:key="user.id" class="collection with-header">
      <li class="collection-item"> {{user.nome}} /{{user.idade}} /{{user.regiao}} /{{user.id}}
        
      </li>
    </ul>
   
    
  </div>
  
</template>

<script>
  import db from './firebaseInit'
  export default {
    name: 'view-user',
    data () {
      return {
        users: []
      }
    },
    created (){
        db.collection('user').get().then(querySnapshot => {
          querySnapshot.forEach(doc=> {
            console.log(doc.id)
            const data = {
              'id': doc.id,
              'id': doc.data().id,
              'nome': doc.data().nome,
              'idade': doc.data().idade,
              'regiao': doc.data().regiao
            }
            this.users.push(data)
          })
            
        })
    
    }
     
  }
</script>

<style scoped>
#view-employee{
  max-width: 400px;
  margin: 0 auto;
  margin-bottom: 100px;
}
</style>
