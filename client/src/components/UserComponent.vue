<template>
  <div class="container mt-4"> 
    <div class="row ">
    <div class="col-sm-5 mx-auto">
     <form  @submit.prevent="Create">
      <div class="mb-3">
        <label for="name" class="form-label">Name</label>
        <input v-model="formreg.name" type="text" class="form-control" id="name" >
      </div>
      <div class="mb-3">
        <label for="surname" class="form-label">Surname</label>
        <input v-model="formreg.surname" type="text" class="form-control" id="surname">
      </div>
      
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">Email address</label>
      <input v-model="formreg.email" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Password</label>
      <input v-model="formreg.password" type="password" class="form-control" id="exampleInputPassword1">
    </div>
    
    <button @click = "Create" type="submit" class="btn btn-dark">Regist</button>
    <p class="error" v-if="error">{{error}}</p>
  </form>
</div>
</div>
</div>
</template>

<script>
import UserService from '../UserService'
export default {
  name: 'UserComponent',
  data () {
    return{
      formreg:{
        name:'',
        surname:'',
        email:'',
       password:'',
      },
       error:''
  }
},
methods:{
  async Create(){
    
    UserService.register(this.formreg.name,this.formreg.surname,this.formreg.email,this.formreg.password)
    .then((response)=>{
    alert(response.data.massage),
    this.$router.push('/')
    })
    
  }
}
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >

</style>
