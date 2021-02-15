<template>
 
   <div class="container-fluid" >
       <br/><br/><br/><br/>
    <div class="col-md-12 col-xs-12 col-sm-12">
       <b-row>         
            <h1 class="titulo">NUESTRAS ACTIVIDADES </h1>            
       </b-row>
        <hr class="hr"/>
    </div>
    <br/><br/>
    <b-row  >    
      <b-col cols="12" lg="3" xl="3" md="3" >        
        <img src="../assets/images/activity.jpg" alt="Mis Garabatos" style="width:90%;margin-top:20%;"/>
      </b-col>     
      <b-col cols="12" lg="1" xl="1" md="1" ></b-col>
      <b-col cols="12" lg="8" xl="8" md="8" >
        
        <div class="col-lg-12 col-md-12 col-sm-12 col-xs-12 "  v-for="item in lActivities" :key="item.id" style="margin-bottom:35px;margin-left:20px;display:table;border-bottom:1px solid black;padding-bottom:10px;" >           
            <b-row>
                <b-col cols="12" sm="12" md="4">
                    <b-img  :src="item.image" width="150" height="150"/>                        
                </b-col>
                <b-col cols="12" sm="12" md="8">
                      <h4>{{item.name}}</h4>    
                    <span style="font-size:18px;">
                    {{item.description}}
                    </span>                                               
                </b-col>                                                                                                                 
            </b-row>      
            <b-row>
              <b-col cols="12" sm="12" md="9"></b-col>
              <b-col cols="12" sm="12" md="3" v-show="item.content.length>0">
                  <b-button type="link" variant="warning" @click="viewActivity(item)">más info</b-button> 
              </b-col>
            </b-row>            
          </div>           
      </b-col>     
    </b-row>
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
      viewActivity(item)
        {
          console.log(item);
            this.$router.push({name:'ActivitiesView',params:{activity:item}});        
        },      
      getActivities()
      {
       let me=this;
            
      let header={"Authorization" : "Bearer " + this.$store.state.token};
      let configuration= {headers : header}; 
                
            axios.get('/api/v1/masters/activities', configuration).then(function(response)
              {                                                                  
                me.lActivities=response.data;
               
                console.log(me.lActivities);
              }).catch(function(error){
                    console.log("ERROR :"+ error);
              });
      }
    }    
  }
</script>
<style>
 .raised{
		-webkit-box-shadow: 0 15px 10px -10px rgba(0, 0, 0, 0.5), 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
		-moz-box-shadow: 0 15px 10px -10px rgba(0, 0, 0, 0.5), 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
				box-shadow: 0 15px 10px -10px rgba(0, 0, 0, 0.5), 0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
}  

.drop-shadow {
		position:relative;
		float:left;
		width:40%;
		padding:1em;
		margin:2em 10px 4em;
		background:#fff;
		-webkit-box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
		-moz-box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
		box-shadow:0 1px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
	}
</style>