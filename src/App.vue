<template>
  <div id="app" class="container-fluid" >   
     <b-container fluid>       
      <NavBar/> 
      <div style="min-height:1200px;">
          <router-view/>        
      </div>
 
      <Pie/>
     </b-container>        
  </div>

      
   
</template>
<script>
import NavBar from '@/components/NavBar.vue'
import Pie from '@/components/Pie.vue'
export default {
    components: {  
      NavBar,
      Pie
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
.card{
-webkit-box-shadow: 10px 10px 31px -6px rgba(255,165,0,1);
-moz-box-shadow: 10px 10px 31px -6px rgba(255,165,0,1);
box-shadow: 10px 10px 31px -6px rgba(255,165,0,1);
margin-left:12px;
}
.hr {border: 0; height: 12px; box-shadow: inset 0 12px 12px -12px orange;}
.texto-descripcion{
  font-size:26px;
  font-family:"Comic Sans MS";
  padding-left:5px;
  color:darkgreen;
}
.texto-pie{
  font-size:20px;
  font-family:"Comic Sans MS";
  padding-left:5px;
  color:darkgreen;
}
</style>
