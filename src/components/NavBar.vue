<template>

  <b-navbar toggleable="lg"  >
    <b-navbar-brand href="#">
      <img src="../assets/images/logonuevopeq.png" />
     
    </b-navbar-brand>
    <span class="d-none d-sm-block" style="font-family:'Comic Sans MS';font-size:48px;margin-left:200px;color:#7E57C2;"> MIS GARABATOS </span>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
    <span class="d-block d-sm-none" style="font-family:'Comic Sans MS';font-size:28px; color:#7E57C2;">MIS GARABATOS</span> 

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
              <b-nav-item href="/" class="fontRed" > 
                <p style="color:#F57C00;">HOME </p>
              </b-nav-item>
              <b-nav-item href="/Proyecto" class="fontRed" >
                <p style="color:#689F38;">  CONOCENOS  </p>
              </b-nav-item>
              <b-nav-item href="/Actividades" class="fontRed">
               <p style="color:#29B6F6;">  ACTIVIDADES </p>
              </b-nav-item>
              <b-nav-item href="/Services" class="fontRed">
                <p style="color:#BA68C8;"> SERVICIOS</p>
              </b-nav-item>
              <b-nav-item href="/ListBlog" class="fontRed">
                <p style="color:#EC407A;"> NUESTRO BLOG</p>
              </b-nav-item>
              <b-nav-item href="/Escuela" class="fontRed">
                <p style="color:#42A5F5;"> NUESTRO ESPACIO</p>
              </b-nav-item>              
              <b-nav-item href="/Contacto" class="fontRed">
                <p style="color:#4DB6AC;"> CONTACTO</p>
              </b-nav-item>        

         
       
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>  
 

</template>

<script>
  export default {
    data() {
      return {
         
      }
    },
    methods:{

        quienes()
        {
          this.$router.push({ path: '/Quienes-Somos' })
          // alert('Quienes somos');
        },
        contact()
        {
          this.$router.push({ path: '/Contacto' })
        }
    }
  }
</script>
<style>
.tittle{
  margin-left:350px;
  font-family:'Comic Sans MS';
  font-size:75px;
  color:rgb(136, 9, 255);  
}

.fontRed{
  font-family: "Comic Sans MS";
  font-size: 22px;
  color: brown;
   }
</style>