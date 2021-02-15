<template>
<div class="container-fluid">
    <b-row>
        <b-col cols="2"></b-col>
        <b-col cols="8">
            <b-row>
                <b-col cols="6"></b-col> 
                <b-col cols="2"> <b-button type="link" variant="warning" @click="back">Volver a Blogs</b-button> </b-col>                           
            </b-row>
        </b-col>
        <b-col cols="2"></b-col>      
    </b-row>
    <b-row>
        <b-col cols="2"></b-col>
        <b-col cols="8">                    
            <b-row>             
                <b-col cols="12">
                    <H3 class="titulo mx-auto">{{article.title}}</H3>
                    <hr class="hr"/>
                </b-col>                          
                <br/> <br/><br/> <br/>
            </b-row>           
            <b-row>
                <b-col cols="2"></b-col>
                <b-col cols="10"> <div v-html="article.texto"/>  </b-col>
            </b-row>                         
        </b-col>
        <b-col cols="2"></b-col>
    </b-row>

</div>
</template>

<script>
export default {
   data() {
      return {
          article:{id:0,categoryId:'',title:'',dateAdd:'',texto:'',resume:'',dateFrom:'',dateTo:'',userAdd:'',user:'',category:''}
      }
    },
    created()
        {
               this.getServices();            
        }, 
    methods:{
        back()
        {
            this.$router.push({name:'ListBlog'});     
        },
        getServices()
        {
             console.log(this.$route.params.article);
             let art=this.$route.params.article;
             if (art!=null)
                 {
                     this.article.id=art.id;
                     this.article.categoryId=art.categoryId;
                     this.article.title=art.title;
                     this.article.dateAdd=art.dateAdd;
                     this.article.texto=art.texto;
                     this.article.resume=art.resume;
                     this.article.dateFrom=art.dateFrom;
                     this.article.dateTo=art.dateTo;
                     this.article.userAdd=art.userAdd;
                     this.article.user=art.user;
                     this.article.category=art.category;
                 }   
        }
    }
}
</script>

<style>

</style>