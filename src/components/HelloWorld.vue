<template>
  <div class="hello" >
  <Formulario></Formulario>
   <table style="width:100%">
  <tr>
    <th>name</th>
    <th>email</th> 
    
  </tr>
  <tr v-for="i in retornaUsuarios" :key="i.id">
    <td>{{i.name}}</td>
    <td>{{i.email}}</td>
    
  </tr>
   </table>


  </div>
   
 

</template>

<script>
import axios from 'axios'
import Formulario from '@/components/Formulario.vue'
export default {
  name: 'HelloWorld',
  components:{
    Formulario
  },
  data () {
    return {
      fields:[
        {key:'name',label:'nombre'},
        {key:'email', label:'email'}
      ],
      name:"",
      email:"",
      users:[],
    }
  },methods:{
    getUsersNode(){
      axios.get('http://localhost:8000/users')
      .then(res=>{
      
        this.users=res.data;
      }).catch((err)=>{
        console.log(err);
      })
    } 
   
  }, computed:{

    retornaUsuarios(){
      return this.users;
    }
  },created(){
this.getUsersNode();
  }
}

</script>

