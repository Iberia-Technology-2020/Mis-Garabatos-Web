<template>
<div class="container-fluid mx-auto">
  <b-row >
      <b-col cols="2">
        <span ></span>
      </b-col>
      <b-col cols="8">
          <b-row>
            <b-col cols="6">
                <H3 class="titulo">{{activity.name}}</H3>          
            </b-col> 
            <b-col cols="2">
                <b-button type="link" variant="warning" @click="back">Volver a Actividades</b-button> 
            </b-col>                                                   
             <hr class="hr"/>
                <br/>  <br/><br/>  <br/>
          </b-row>
          <b-row>
              <b-col cols="1"></b-col>
              <b-col cols="9"><div v-html="activity.content"/></b-col>
              <b-col cols="2"></b-col>
          </b-row>

      </b-col>
      <b-col cols="2"><span></span></b-col>
  </b-row>
</div>

</template>

<script>
export default {
   data() {
      return {
      activity:{id:0,image:'',name:'',description:'',content:'',title:''}
      }
    },
    created()
        {
          this.getActivities();            
        }, 
    methods:{
        back()
        {
            this.$router.push({name:'Actitivities'});     
        },
        getActivities()
        {
             console.log(this.$route.params.activity);
             let act=this.$route.params.activity;
             if (act!=null)
                 {
                     this.activity.image=act.image;
                     this.activity.title=act.title;
                     this.activity.name=act.name;
                     this.activity.description=act.description;
                     this.activity.content=act.content
                 }   
        }
    }
}
</script>

<style>

</style>