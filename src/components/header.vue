<template>
     <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Название: </span>
        <span class="font-weight-light">Тестовое задание №5</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
         <v-btn
         v-if="showRoutes == true"
        flat
       @click="toRoute('/sign_up')"
      >
        <span class="mr-1">Sign up</span>
      </v-btn>
       <v-btn
         v-if="showRoutes == true"
        flat
       @click="toRoute('/auth')"
      >
        <span class="mr-1">Login</span>
      </v-btn> <v-btn
         v-if="!showRoutes "
        flat
       @click="toRoute('/')"
      >
        <span class="mr-1">Home</span>
         </v-btn> <v-btn
         v-if="showRoutes "
        flat
       @click="toRoute('/users')"
      >
        <span class="mr-1">Users</span>
      </v-btn>
    </v-toolbar>
</template>

<script>
export default {
  props: ['showRoutes'],

  methods:{
    toRoute(route){
      this.$router.push(route)
    }
}
}
</script>


