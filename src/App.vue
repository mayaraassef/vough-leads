<template>
  <div id="app">
    <logo />
    <h1>Lista de clientes</h1>
    <input type="text" placeholder="buscar cliente pelo nome" v-model="busca">
    <button @click="buscar">Buscar</button>
    <div v-for="(person,index) in filteredClientes" :key="index">
      <clientes :name="person.name" :username="person.username" :email="person.email" :address="person.address" :city="person.city" :website="person.website"
      :company="person.company" :bs="person.bs"/>

    </div>
    
  </div>
</template>

<script>
import axios from 'axios';
import clientes from './components/clientes';
import logo from './components/logo';

export default {
  name: 'App',
  data(){
    return {
      clientes: [],
      filteredClientes:[],
      busca: ''
    }
  },
  created: function(){
    axios.get("https://jsonplaceholder.typicode.com/users").then(res => {
      this.clientes = res.data;
      this.filteredClientes = res.data;
    })
  },
  components:{
    clientes,
    logo
  },
  methods:{
    buscar: function(){
      this.filteredClientes = this.clientes;
      if(this.busca == '' || this.busca == ' '){
       this.filteredClientes = this.clientes;
      }else{
        this.filteredClientes = this.clientes.filter(cliente => cliente.name.match(this.busca));


        }
      }
    }, 
    
    
}

  

</script>

<style>

h1{
  text-align: center;
}

input {
  margin:auto;
  margin-bottom: 5px;
  margin-right: 5px;
  text-align: center;
  font-size: 20px;
  border: 3px solid cyan;
}

button {
  font-size: 20px;
  background-color: cyan;
  border-radius: 5px;
  font-weight: bold;
}


</style>
