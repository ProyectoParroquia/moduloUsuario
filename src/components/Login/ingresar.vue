<template>
    <v-card-text class="mt-12">
                        <h1
                          class="text-center display-10 purple--text text--light2"
                        >Iniciar sesion</h1>
                        <div class="mt-6">
                            <v-alert
                              margin="3"
                              dense
                              elevation="15"
                              prominent
                            role="alert" v-if="error"
                              border="left"
                              color="pink darken-1"
                              dark
                            >
                          {{error_msg}}
                          </v-alert>
                        </div>
                              
                        <v-form v-on:submit.prevent="login">
                          <v-text-field
                           v-model="username"
                            label="Usuario"
                            name="Usuario"
                            prepend-icon="person"
                            type="text"
                            color="#ae5f9e"
                          />

                          <v-text-field
                            v-model="password"
                            id="password"
                            label="Password"
                            name="password"
                            prepend-icon="lock"
                            type="password"
                            color="#ae5f9e"
                          />
                          <div class="text-center my-3 ">
                            <v-btn type="submit" block rounded color="#ae5f9e" dark>Ingresar</v-btn>
                          </div>
                          
                        </v-form>
                        <div class="text-center mt-3">
                          <button v-on:click="close()">
                          <h3 class="text-center mt-4">¿Olvidaste tu contraseña?</h3>
                        </button>
                        </div>
                        
                      </v-card-text>
</template>
<script>
import axios from 'axios';
export default {
   data: function(){
     return {
      
      username: "",
      password: "",
      error: false,
      error_msg: "",
    }
  },

  methods:{
    login(){
        let json = {
          //this para llamar a una funcion a una variable de la misma clase           
          "username" : this.username,
          "password": this.password
        };
        axios.post('http://localhost:3000/api/credenciales/login/', json)
        //eso devuelve una promesa
        .then( respuesta =>{
          console.log(respuesta)
           if(respuesta.status === 201){
             
             localStorage.token = respuesta.data.success;
             this.$router.push('/about');
           }else{
             this.error = true;
             this.error_msg = respuesta.data.error;
           }
        })
    }
  }
};
</script>
