<template>
  <div class="container-fluid">
    <b-overlay :show="show" rounded="sm">
        <b-row class="my-1">
          <b-col sm="2">
            <label for="input-small">Nombre:</label>
          </b-col>
          <b-col sm="10">
            <b-form-input id="name" size="sm" placeholder="Introduzca su nombre y apellido" v-model="form.name"></b-form-input>
          </b-col>
        </b-row>
        <b-row class="my-1">
          <b-col sm="2">
            <label for="input-small">Email :</label>
          </b-col>
          <b-col sm="10">
            <b-form-input id="email" size="sm" placeholder="Introduzca su email "  type="email" v-model="form.email"></b-form-input>
          </b-col>
        </b-row>
        <b-row class="my-1">
          <b-col sm="2">
            <label for="input-small">Telefono:</label>
          </b-col>
          <b-col sm="10"> 
            <b-form-input id="phone" size="sm" placeholder="Introduza su telefono" type="number" v-model="form.phone"></b-form-input>
          </b-col>
        </b-row>
        <b-row class="my-1">
          <b-col sm="2">
            <label for="input-small">Mensaje :</label>
          </b-col>
          <b-col sm="10">
            <b-form-textarea id="text" placeholder="Texto libre"  rows="8" v-model="form.message"></b-form-textarea>
          </b-col>
        </b-row>      
        <b-row>
            <b-col>
                  <b-form-checkbox id="chkOk" v-model=status name="chkOk" :value="false" :unchecked-value="true">
                    Acepto las condiciones de uso y la GDPR
                  </b-form-checkbox>          
            </b-col>
        </b-row>
        <br/>
        <hr/>
        <b-row class="my-1">
            <b-col sm="3"> <b-button type="reset" variant="danger">Reset</b-button> </b-col>
            <b-col sm="6"> </b-col>
            <b-col sm="3"> <b-button type="send" variant="success" @click="send" >Enviar</b-button> </b-col>       
        </b-row>
     </b-overlay>        
  </div>              
</template>

<script>
import axios from 'axios'
export default {
      data() {
      return {
          status:false,
        form: {
          email: '',
          name: '',
          phone:'',
          message:'',         
        },       
        show: false
      }
    },
    methods: {

     makeToast() {
        this.$bvToast.toast('Email enviado correctamente', {
          title: `MIS GARABATOS`,
          variant: "success",
          solid: true
        })
      },
     reset()
     {
       this.form.nam='';
       this.form.phone='';
       this.form.email='';
       this.form.message='';
     },
     send()
      {
        this.show=true;
          axios.post('/api/v1/email/contact',{'name':this.form.name,'email':this.form.email,'phone':this.form.phone,'message':this.form.message
              }).then(function(response)
                  {                
                     console.log(response);                                
                    }).catch(function(error){
                        console.log('error '+error);
                    });
         this.show=false;
         this.makeToast();     
      }
    }
}
</script>

<style>

</style>