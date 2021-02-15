<template>
  <div>
    <div class="col-md-12 col-sm-12 col-xs-12">
      <H3 class="titulo">ACTIVIDADES</H3>
      <hr class="hr"/>
    </div>
   <div class="col-md-12 col-sm-12 col-xs-12">
      <b-list-group v-for="item in lActivities" :key="item.id">        
          <b-list-group-item href="#">              
              <b-img  :src="item.image" width="100" height="100"/>
                <span class="texto-descripcion">  {{item.name}}  </span>
          </b-list-group-item>               
      </b-list-group>               
   </div>    
  </div>

</template>

<script>
import axios from 'axios'
  export default {
    data() {
      return {
        lActivities:[]
       
      }
    },    
  created()
        {
            this.getActivities();            
        },     
  methods:{

        getActivities()
        {
             console.log('listando actividades');
            let me=this;
            let header={"Authorization" : "Bearer " + this.$store.state.token};  
            let configuration= {headers : header};        
            axios.get('/api/v1/masters/activities',configuration).then(function(response)
                {                                                           
                    me.lActivities=response.data;
                   
                    console.log(me.lActivities);
                        
                }).catch(function(error){
                        console.log(error);
                });        
          
        },
        contact()
        {
          this.$router.push({ path: '/Contacto' })
        }
    }    
    
  }
</script>
<style>
.titulo{
      display: block;
      -webkit-box-sizing: content-box;
      -moz-box-sizing: content-box;
      box-sizing: content-box;
      float: none;
      z-index: auto;
      width: auto;
      height: auto;
      position: static;
      cursor: default;
      opacity: 1;
      margin: 0;
      padding: 0;
      overflow: visible;
      border: none;
      -webkit-border-radius: 0;
      border-radius: 0;
      font: italic normal bold 32px/normal "Comic Sans MS", cursive, sans-serif;
      color:rgba(217,14,240,1);
      -o-text-overflow: ellipsis;
      text-overflow: ellipsis;
      letter-spacing: 2px;
      white-space: nowrap;
      word-spacing: 2px;
      background: none;
      -webkit-box-shadow: none;
      box-shadow: none;
      text-shadow: 2px 2px 2px rgba(0,0,0,0.5) ;
      -webkit-transition: none;
      -moz-transition: none;
      -o-transition: none;
      transition: none;
      -webkit-transform: none;
      transform: none;
      -webkit-transform-origin: 50% 50% 0;
      transform-origin: 50% 50% 0;
}
.hr {border: 0; height: 12px; box-shadow: inset 0 12px 12px -12px orange;}
</style>