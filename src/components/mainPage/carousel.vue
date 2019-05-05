<template>
      <v-carousel style="min-width:85vw">
                    <v-carousel-item
                    v-for="(item,i) in items"
                    :key="i"
                    :src="item.src"
                    ></v-carousel-item>
     </v-carousel>
</template>

<script>
export default {
  data(){
      return {
         items: [
                {
                    src: 'https://cdn.vuetifyjs.com/images/carousel/planet.jpg'
                },
               {
                  src: 'https://images.pexels.com/photos/1838471/pexels-photo-1838471.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940'
              },
              {
                  src: 'https://images.pexels.com/photos/425197/pexels-photo-425197.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940'
              },
              {
                  src: 'https://images.pexels.com/photos/1842417/pexels-photo-1842417.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940'
              },
             
          ]
      }
  }
  
}
</script>

