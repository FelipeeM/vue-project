<template>
 <div id="form-base">
    <h3>Editar ou Deletar selecionando o ID</h3>
    <div class="row">
    <form @submit.prevent="updateEmployee">
      <div class ="input-container">
          <label for="nome">Nome: </label>
          <input type="text" v-model="nome" placeholder="Digite seu nome">
            </div>
            <div class ="input-container">
              <label for="id">Id: </label>
              <input type="text" v-model="id" placeholder="Digite seu ID">
            </div>
            <div class ="input-container">
              <label for="idade">Idade: </label>
              <input type="text" v-model="idade" placeholder="Digite sua idade">
            </div>
            <div class ="input-container">
              <label for="regiao">Região: </label>
              <input type="text" v-model="regiao" placeholder="Digite sua região">
            </div>
            <div class ="input-container-2">
            <button type="submit" class="btn-floating btn-large blue">
              <i class="fa fa-pencil"></i>
            </button>  
            <button @click="deleteEmployee" type="submit" class="btn-floating btn-large blue">
              <i class="fa fa-trash-o" ></i>
            </button>                           
        </div>
    </form>
  </div>
  </div>
</template>

<script>
  import db from './firebaseInit'
  export default {
    name: 'edit-user',
    data () {
      return {
        id: null,
        nome: null,
        idade: null,
        regiao: null
      }
    },
    methods: {
      deleteEmployee () {
        
          db.collection('user').where('id', '==', this.id).get().then((querySnapshot) => {
            if(confirm ('Tem certeza que deseja apagar?')){
            querySnapshot.forEach((doc) => {
              console.log(doc.ref)
              doc.ref.delete();
              this.$router.push('/')
            })
            }
          })
        
      },
      updateEmployee () {
       
        db.collection('user').where('id', '==', this.id).get().then((querySnapshot) => {
          querySnapshot.forEach((doc) => {
            doc.ref.update({
              id: this.id,
              nome: this.nome,
              idade: this.idade,
              regiao: this.regiao
            })
            .then(docRef => {
            console.log('Client update: ', docRef.id)
            
          })
          .catch(error => {
            console.error('Error adding employee: ', error)
          })
          })
        })
      }
    }
  }
  
</script>
<style scoped>

#form-base{
    max-width: 400px;
    margin: 0 auto;
}

.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}
.input-container-2{
    float:right;
    flex-direction: column;
    margin-bottom: 20px;
}
label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid rgb(66, 140, 224);
}
input, select {
    padding: 5px 10px;
    width: 300px;
}
.submit-btn {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
}

.submit-btn:hover{
     background-color: transparent;
     color:#222;
}

</style>