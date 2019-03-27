<template>
    <div>
      <h1> Get All User </h1>
      <div v-for="user in users" v-bind:key="user.id" >
         <p>จำนวนผู้ใช้งาน {{ users.length }}</p>
         <p>id : {{ user.id }}</p>
         <p>ชื่อ-นามสกุล : {{ user.name }} - {{ users.lastname }}  </p>
         <p>Email : {{ user.email }}</p>
         <p>password : {{ users.password }}</p>
         <p><button v-on:click="navigateTo('/user/'+user.id)">ผู้ใช้งาน </button></p>
         <hr>
      </div>
    </div>
</template>

<script>
import UsersService from '@/services/UsersService'

export default {
   data () {
     return {
       users :[]
     }
   },
   async created () {
      this.users = (await UsersService.index()).data
   },
   methods:{
     navigateTo (route) {
       this.$router.push(route)
     }
   }
}
</script>
<style scoped>

</style>


