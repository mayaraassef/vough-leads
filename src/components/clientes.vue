<template>
  <div>
      <div class="box">
      <h3>{{num}} Nome: {{name}}</h3>
      <h3> Usuário: {{username}}</h3>
      <h3>E-mail: {{email}}</h3>
      <h3> Cidade: {{address.city}}</h3>
      <h3> Site: {{website}}</h3>
      <h3> Categoria da empresa: {{company.bs}}</h3>
      </div>
      
  </div>

</template>

<script>


export default {


    data(){
        return {
            cliente: {}
        }
    },

    props: {
        num: Number,
        name: String,
        username: String,
        email: String,
        address: Object,
        website: String,
        company: Object
    }
}
</script>

<style>

    .box{
        border: 5px solid cyan;
        margin: auto;
        padding: 5px;
        text-align: center;
         margin-bottom:5px;
    }
</style>



