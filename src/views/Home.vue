<template>
 <v-app light>
   <main-header />
  <first-section />
  <second-section />
  
   <third-section />
   <main-footer/>
 </v-app>
</template>

<script>
  import firstSection from '../components/mainPage/firstSection'
   import secondSection from '../components/mainPage/secondSection'
   import thirdSection from '../components/mainPage/thirdSection'
     import mainFooter from '../components/mainPage/footer'
       import mainHeader from '../components/header'

  export default {
    components: {
      firstSection,
       secondSection,
       thirdSection,
       mainFooter,
       mainHeader
    }
  }
</script>
