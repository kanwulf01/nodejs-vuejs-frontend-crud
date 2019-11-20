<template>
  <div>

      <form>
          <fieldset>
              <legend>Formulario</legend>
              <label>Insert Name</label>
              <input v-model="date.name" aria-placeholder="Name" required>
              <label>Insert Email</label>
              <input v-model="date.email" aria-placeholder="Email" required>
          </fieldset>
      </form>
              <button class="btn btn-success" @click="InsertUserNode()">Make Query Post</button>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  data(){
    return{
      date:{
      name:null,
      email:null,
      }
    }
  },
methods:{
    InsertUserNode(){
      axios.post('http://localhost:8000/users',this.date)
      .then(res=>{
        alert(res.data)
      }).catch((err)=>{
        console.log(err)
      })
      
    },
}
}
</script>

<style>

</style>