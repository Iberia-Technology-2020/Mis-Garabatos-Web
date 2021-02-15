<template>
 <div class="container-fluid" >
       <br/><br/><br/><br/>
    <div class="col-md-12 col-xs-12 col-sm-12">
        <h1 class="titulo">CONTACTANOS  </h1>
        <hr class="hr"/>
    </div>
    <br/><br/>
     <b-row>
         <b-col cols="12" lg="6" xl="6" sm="12" md="6" xs="12">  
             <div style="border solid 1px;">
                  <gmap-map :center="center" :zoom="16" style="width:100%;  height: 600px;" >
                      <gmap-marker :key="index" v-for="(m, index) in markers" :position="m.position"  @click="center=m.position"></gmap-marker>
                  </gmap-map>
              </div>
      
         </b-col>
         <b-col cols="12" lg="6" xl="6" sm="12" md="6" xs="12">
            <div>               
                <b-tabs pills card>
                  <b-tab title="Donde Estamos" active>
                    <DondeEstamos/>
                   </b-tab>
                  <b-tab title="Contacto"> <b-card-text><FormContact/></b-card-text></b-tab>
                  <b-tab title="Solicitud de Plaza"><b-card-text><pre-inscription/></b-card-text></b-tab>
                </b-tabs>
            
            </div>           
         </b-col>         
     </b-row>
 </div>

</template>

<script>
import FormContact from '@/components/FormContact.vue'
import PreInscription from '@/components/PreInscription.vue'
import DondeEstamos from '@/components/DondeEstamos'
export default {
  name: "Contact",
 components: {  
            FormContact,
            PreInscription,
            DondeEstamos
       },  
  data() {      
    return {
      // default to montreal to keep it simple
      // change this to whatever makes sense
      center: { lat:40.32974, lng: -3.85396 },
      markers: [{
          id:0,
          position: {lat:40.32974, lng: -3.85396 },
          title: "Escuela Infantil Mis Garabatos  Mostoles - Madrid"
        }],
      places: [],
      currentPlace: null
    };
  },

  mounted() {
  //  this.geolocate();
  },

  methods: {

  }
};
</script>

<style>

</style>