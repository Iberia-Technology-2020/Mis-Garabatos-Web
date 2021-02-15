<template>
 <div class="col-md-12 col-sm-12 col-xs-12" style="margin-top:150px;">
     <b-row>
       <div class="col-md-6 col-sm-6 col-xs-12">
            <H3 class="titulo">NUESTRO BLOG DE NOTICIAS</H3>
          
       </div>
       <div class="col-md-3 col-sm-3 col-xs-12">
          <b-form-input v-model="search" placeholder="introduzca el texto a buscar" @input="filteredText"></b-form-input>
       </div>       
       <div class="col-md-3 col-sm-3 col-xs-12">
          <b-form-select v-model="selected" :options="lCategories"  value-field="name" text-field="name" @change="filteredCategories"></b-form-select>
       </div>              
     </b-row>
     <b-row>
         <div class="col-md-12 col-sm-12 col-xs-12">
               <hr class="hr"/>
         </div>
     </b-row>
     <br/><br/>
       <b-overlay :show="show" rounded="sm">
          <b-row>      
                <div class="col-md-1 col-sm-1 col-xs-12"></div>     
                <div class="col-md-10 col-sm-10 col-xs-12">
                    <b-row >
                      <div class="col-md-5 col-sm-5 col-xs-12"  style="border-right:solid 1px #DDDEDF;border-bottom:solid 1px #DDDEDF;display:block;" v-for="a in lBlogsFiltered" :key="a.id">              
                        <b-row>
                            <b-col cols="4">
                                <img  src="../assets/images/logonuevo.png" width="150" height="150"/>
                            </b-col>
                            <b-col cols="8">
                                <h2    >{{a.title}}</h2>
                                <h6>Categoría: {{a.category}}</h6>
                                <span> {{a.resume}}</span>
                            </b-col>
                            <b-col cols="9"><span>Autor : {{a.user}} </span> </b-col>
                            <b-col cols="3" v-show="a.texto.length>0">
                                  <br/> 
                                  <b-button type="link" variant="warning" @click="viewActivity(a)">más info</b-button>
                                  <br/><br/>
                            </b-col>                 
                        </b-row>              
                      </div>
                      
                    </b-row>         
                </div>
                <div class="col-md-1 col-sm-1 col-xs-12"></div>      
          </b-row>
       </b-overlay>
 </div>  
</template>

<script>
import axios from 'axios'
  export default {
    data() {
      return {
         lCategories:[],
         lBlogsFiltered:[],
         lblogs:[],
         search:'',
         selected:'',
         show:true
      }
    },
    created()
        {
            this.getCategories();          
            this.listBlog();  
        },     
    methods:{
      filteredText()
      {
        console.log(this.search);
        if (this.selected=='')
          this.lBlogsFiltered=this.lBlogs;
        else
          this.lBlogsFiltered=this.lBlogs.filter(x=>x.resume.contains(this.search));
      },
      viewActivity(item)
      {
        console.log(item);
        this.$router.push({name:'BlogView',params:{article:item}});
      },
     filteredCategories()
     {       
       
      if (this.selected=='--')
        this.lBlogsFiltered=this.lBlogs;
      else
        this.lBlogsFiltered=this.lBlogs.filter(x=>x.category==this.selected);
     },
    listBlog()
    {
      let me=this;
            
      let header={"Authorization" : "Bearer " + this.$store.state.token};
      let configuration= {headers : header}; 
                
            axios.get('api/v1/blogs/articles', configuration).then(function(response)
              {                                                                  
                me.lBlogs=response.data;
                me.lBlogsFiltered=me.lBlogs;
                me.show=false;
                console.log(me.lBlogs);
              }).catch(function(error){
                    console.log("ERROR :"+ error);
              });
    },     
    getCategories()
        {
            console.log('listando Categorias');
            let me=this;
            let header={"Authorization" : "Bearer " + this.$store.state.token};
            let configuration= {headers : header};        
            axios.get('/api/v1/masters/categories',configuration).then(function(response)
                {   
                   console.log(response.data)                                                        ;
                    me.lCategories=response.data;
                 //   me.lCategoriesFiltered=me.lCategories;
                    
                        
                }).catch(function(error){
                        console.log(error);
                });
        }
    }
  }
</script>
<style>


</style>