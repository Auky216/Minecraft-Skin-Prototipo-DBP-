<script>

import {ref} from 'vue'

export default {

  name: "App",

  data(){
    return {
      name: "Adrian Auqui",
      listaSkin : ref([]),
      boolShow : false,
      username : "",
      usernamePop : ""
    }
  },
  methods :{
    AddUser(){
      if(!this.listaSkin.includes(this.username)) {
        this.listaSkin.push(this.username);
      }
      console.log(this.username)
    },
    ShowTable(){
      this.boolShow = true;
    },
    inputUsername(e) {
      this.username = e.target.value;
    },
    inputDeleteUsername(e){
      this.usernamePop = e.target.value;
    },
    DeleteUsername(){
      this.listaSkin.pop(this.usernamePop);
    }
  }
  
}
</script>



<template>
  <h1>Minecraft Skin</h1>
  

  <div class="form-floating mb-3">
  <input @input="inputUsername" type="text" class="form-control" :value="username">
  <label for="floatingInput">Username</label>
  <br>
  <button  @click="AddUser" class="btn btn-primary">Agregar</button>
  <br>
  <br>
    
  </div>

  <div class="form-floating mb-3">
  <input @input="inputDeleteUsername" type="text" class="form-control" :value="usernamePop">
  <label for="deleteusername">Detelete Username</label>
  <br>
  <button  @click="DeleteUsername" class="btn btn-primary">Delete</button>
  <br>
  <br>
  
  
  </div>


  <button  @click="ShowTable" class="btn btn-primary"> Mostrar Tabla </button>

  
  
   

    

    
  
  

  <table v-if="boolShow === true" class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">User</th>
      <th scope="col">Skin</th>      
    </tr>
  </thead>
  <tbody v-for="(usr,index) in listaSkin" :key="index">
    <tr>
      <th scope="row">{{index + 1}}</th>
      <td>{{usr}}</td>
      <td>
        <img :src="'https://mineskin.eu/head/'+usr+'/100.png'">
      </td>      
    </tr>
  </tbody>
</table>>


</template>


<style>

h1{
  color: rgb(8, 195, 136);
}

</style>

