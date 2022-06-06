
<template>

  <div id="app">
    
     <div id="main-container">
    <Texts :dados="'preencha esse formulario para comcluir seu cadasto'" />
    <h1>abra sua conta</h1>
    <form id="app" @submit.prevent="checkForm">
 
    <div class="texto">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Orci, volutpat
        in iaculis nec nibh nisl tellus.
      </p><br />
      </div>

        <div class="full-box">
        <label for="nome completo">nome completo: </label><br />
        <input 
          id="name"
          v-model="name"
          type="text"
          name="name"
          placeholder="Nome completo"
        />

        <p v-if="errorNameEmpty" class="textError">Nome não pode estar vazio</p>

        <p v-if="errorNameLength" class="textError">
          Nome deve ter pelo menos 5 caracteres
        </p>
      </div>

      <div class="half-box">

        <label for="email">E-mail</label><br/>
        <input id="email" v-model="email" type="text" placeholder="E-mail" />
        <p v-if="errorEmail" class="errorEmail">
          E-Mail não pode estar vazio
        </p>
        <br />
      </div>

      <div class="half-box">
        <label for="email2">confirme seu e-mail:</label><br />
        <input id="email2" v-model="email2" type="text" placeholder="E-mail" />
        <br />
        <p v-if="errorEmail" class="textError">E-mail invalido</p>
      </div>

      <div>
        <label for="CPF">CPF:</label><br />
        <input type="text" v-model="CPF" id="cpf" placeholder="CPF" />
        <br />
          <p v-if="errorEmail" class="textError">CPF invalido</p>
      </div>

      <div class="half-box">
        <label for="celular">Celular:</label><br />
        <input type="tel" id="celular" name="celular" placeholder="celular" />
 
          <p v-if="errorEmail" class="textError">Numero de telefone invalido</p>
      </div>

      <div>
        <label for="data">data de nascimento:</label>
        <input type="date" id="date" name="data" />
          <p v-if="errorEmail" class="textError">Data de nascimento invalida</p>
      </div>

       <div class="texto">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Orci, volutpat
        in iaculis nec nibh nisl tellus.
      </p>
      </div><br />

      <div class="full-box">
        <input type="checkbox" id="sms" name="sms" value="sms" />
        <label for="sms">SMS e E-mail</label>
      </div>

      <div class="full-box">
        <input type="checkbox" id="whatsapp" name="whatsapp" value="whatsapp" />
        <label type="checkbox" for="whatsapp">WhatsApp</label>
      
      </div>

      <div>  <input type="submit" value="continuar" /></div>

    </form>
  </div>
  </div>
</template>

<script>
/*import axios from 'axios'*/
import Texts from "./component/Texts.vue"

export default {
  
  name: "App",

  components: {
    
    Texts,
  },

  data() {
    return {
      errorNameEmpty: false,
      errorNameLength: false,
      errorData: false,
      errorEmail: false,
      name: null,
      email: null,
      CPF: null
    };
  },

  methods: {
    checkForm() {
    
      if (!this.name) {
        this.errorNameLength = false;
        this.errorNameEmpty = true;
         console.log("estou aqui")
      } else if (this.name.length < 5) {
        this.errorNameEmpty = false;
        this.errorNameLength = true;
      } else {
        this.errorNameEmpty = false;
        this.errorNameLength = false;
      }

      const emailRegex = /^[a-z0-9.]+@[a-z0-9]+\.[a-z]+(\.[a-z]+)?$/i;
      if (!emailRegex.test(this.email)) {
        this.errorEmail = true;
      } else {
        this.errorEmail = false;
      }
      if (this.email !== this.confirmemail) {
        this.errorConfirmEmail = false;
      } else {
        this.errorConfirmemail = false;
      }

      if (!this.cellphone) {
        this.errorCellphoneLength = false;
        this.errorCellphoneEmpty = true;
      } else if (this.cellphone.length < 14) {
        this.errorCellphoneEmpty = false;
        this.errorCellphoneLength = false;
      }
     
    },
  },
};

</script>


<style>

*{
margin: 0;
padding: 0;
box-sizing: border-box;
border: none;
}

#app {
 font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ff006a;
  margin-top: 60px;
  }

.texto{
  color: rgb(0, 0, 0);
}

 input, label{
   display: block;
   width: 100%;
 }

input:focus, label:focus{
 outline:none ;
}

a{
  color: rgb(207, 0, 79);
}

body{
padding-top: 0vh; 
background-image: url('../img/abra\ sua\ conta.\ \(2\).png') ;
background-size:cover ;
background-image: 90%;
}

#main-container{
 width: 500px;
 margin-left: auto;
margin-right: auto;
background-color: #ffffff;
border-radius:70px ;
padding: 50px;


}

#main-container h1{
 text-align: center;
 margin-bottom:5px;
 font-size: 1.6rem;
}

form{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
  
.full-box{
 flex:1 1 100% ;
 position: relative;
}

.hall-box{
  flex:1 1 45% ;
 position: relative;
}




</style>
