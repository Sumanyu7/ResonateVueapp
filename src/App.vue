<template>
    <div class="container pt-5">
      <h2>Resonate Solutions Test</h2>
      <h1 class="py-3 text-center gradient">Contacts</h1>
      <table class="table table-striped table-hover table-bordered table-responsive text-center "> 
              <thead class="text-white"> 
                  <th>ID</th> 
                  <th>Name</th> 
                  <th>Email</th> 
                  <th>Address</th> 
                  <th >Company</th> 
                  <th>Website</th> 
              </thead> 
              <tbody v-cloak> 
                  <tr v-for="a in users" :key="a.id" > 
                      <td>{{a.id}}</td> 
                      <td>{{a.name}}</td> 
                      <td>{{a.email}}</td> 
                      <td>{{a.address.suite}}<br>{{a.address.street}}<br>{{a.address.city}} </td> 
                      <td>{{a.company.name}}</td> 
                      <td><a :href="'//' + a.website" target="_blank">{{a.website}}</a></td>
                  </tr> 
              </tbody> 
          </table> 
      </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  components: {
  
  },
  data: () => ({
    users: null
  }),
  created: function () {
    this.fetchUsers();
  },
  methods: {
      fetchUsers: function () {
          axios.get("https://jsonplaceholder.typicode.com/users").then((result) => {
          this.users = result.data;
        })
      } 
  }
}

</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.gradient{
  background: -webkit-linear-gradient(90deg, #009879, #471b64);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
.container .table-hover tr:hover{
  color:#009879;
  font-weight: bold;
}
.container table{
  max-width:100%;
}
  .container table thead{
    background: linear-gradient(90deg, #009879, #471b64);
  }
    .container table thead th{
      padding:10px;
      font-size:20px;
    }

</style>
