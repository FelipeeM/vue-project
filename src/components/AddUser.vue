<template>
  <div id="form-base" >
        <h3>Adicionar</h3>
        <div>
            <form  @submit.prevent="saveEmployee" class="col s12" >
                <div class ="input-container">
                    <label for="nome">Nome: </label>
                    <input type="text" v-model="nome" placeholder="Digite seu nome" required>
                </div>
                <div class ="input-container">
                    <label for="id">Id: </label>
                    <input type="text" v-model="id" placeholder="Digite seu ID" required>
                </div>
                <div class ="input-container">
                    <label for="idade">Idade: </label>
                    <input type="text" v-model="idade" placeholder="Digite sua idade" required>
                </div>
                <div class ="input-container">
                    <label for="regiao">Região: </label>
                    <input type="text" v-model="regiao"  placeholder="Digite sua região" required>
                </div>
                   
                   <div class ="input-container-2">
                        <button type="submit"  class="btn-floating btn-large blue">
                            <i class="fa fa-plus" ></i>
                        </button>                       
                   </div>
            </form>
        </div> 
     </div>    
</template>
<script>
import db from './firebaseInit'

export default {
    name: 'add-user',
    data(){
        return{
            nome: null,
            idade: null,
            regiao: null,
            id: null
        }
    },
    methods: {
        saveEmployee () {
          db.collection('user').add({
            id: this.id,
            nome: this.nome,
            idade: this.idade,
            regiao: this.regiao
          })
          .then(docRef => {
            console.log('Client added: ', docRef.id)
            
          })
          .catch(error => {
            console.error('Error adding employee: ', error)
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
    color: rgb(66, 140, 224);
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