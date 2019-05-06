<template>
  <v-app light>
    <main-header :showRoutes="true"/>
    <v-layout column align-center justify-center>
      <v-card  align-center justify-center >
            <table>
            <tr>
            <th>number</th>
            <th>Name</th>
            </tr>
            <tr
            v-for="(user,i) in users" :key="i">
                <td>
                    {{i}}
                </td>
                <td>{{user.username}}</td>
            </tr>
            </table>

      </v-card>
      <v-btn primary @click="getUsers">Клик</v-btn>
    </v-layout>
  </v-app>
</template>

<script>
import mainHeader from "../components/header";
import axios from "axios";
export default {
  components: {
    mainHeader
  },
  methods: {
    async getUsers() {
      const users = await axios.get("/auth/getAll");
      
      this.users =  users.data.data  
    }
  },
  data() {
    return {
      users: []
    };
  },
  mounted(){
    
  }
};
</script>

<style>
table {
border: 1px solid #69c;
border-collapse: collapse;
empty-cells: hide;
margin: 2em;
}
th, td {border: 2px solid #69c;}
td{ padding: 5px;}
</style>
