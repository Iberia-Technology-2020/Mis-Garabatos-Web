<template>
  <b-carousel id="carousel-fade" style="text-shadow: 0px 0px 2px #000;border-radius:9px;" :interval="2000"  fade indicators >          
    <b-carousel-slide class="d-block img-fluid w-100" v-for="item in lCovers" :key="item.id" :caption="item.title">
        <template v-slot:img>
                <img
                class="d-block class-name"
                width="90%"
                height="35%"      
                :src="item.image"
                style="color:item.colorTitle"
                alt="image slot"/>
        </template>
    </b-carousel-slide>     
  </b-carousel>
</template>

<script>
 import axios from 'axios'
  export default {
    data() {
      return {
         lCovers:[]
      }
    },
    created()
        {
            this.getCovers();            
        },     
    methods:{
      getCovers()
        {
            console.log('listando portadas');
            let me=this;
              
            axios.get('/api/v1/covers/web').then(function(response)
                {                                                           
                  me.lCovers=response.data;
                  me.lCoversFilters=me.lCovers;
                  console.log(me.lCovers);                        
                }).catch(function(error){
                        console.log(error);
                });
        }
    }
  }
</script>
<style>


</style>