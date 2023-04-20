<template>
  <div class="container">
    <div class="item">

      <h2>PASO {{ step }}</h2>
      <strong>{{ error }}</strong>
    </div>
    <div class="content">
      <input type="text" v-model="email" placeholder="Email">
      <input type="password" v-model="contraseña" placeholder="Contraseña">
          <input type="password" v-model="contraseñaConfirm" placeholder="Confirmar contraseña" >
          <input type="number" v-model="numeroTel" placeholder="Numero Télefono" >
          <input type="number" v-model="numerocel" placeholder="Numero Celular" >
        
      </div>
      <div class="itembtn">
       
        <a @click="onSubmit">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      SIGUIENTE
    </a>
    <a @click="onBack">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      ANTRÁS
    </a>
      </div>
  </div>
</template>

<script lang="ts">
import { thisExpression } from '@babel/types';

export default {
  props: {
    step: Number
  },
  data() {
    return {
      email: '',
      contraseña: '',
      contraseñaConfirm: '',
      numeroTel: 0,
      numerocel: 0,
      error: null
    }
  },
  methods: {
    isValidEmail(email) {
      // Expresión regular para validar el formato de correo electrónico
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      return emailRegex.test(email);
    },
    onSubmit() {
      if (!this.email || !this.contraseña || !this.contraseñaConfirm || !this.numeroTel || !this.numerocel) {
        this.error = 'Por favor, completa todos los campos';
      } else if(this.isValidEmail(this.email)){
          if( this.contraseña === this.contraseñaConfirm){
            this.error = null;
            this.$emit('next-step', { email: this.email, contraseña: this.contraseña, contraseñacon: this.contraseñaConfirm, numerotel: this.numeroTel, numerocel: this.numerocel });
          }else{
            this.error = "Las contraseñas no coinciden";
          }
        }else {
          this.error = 'El formato del correo es incorrecto';
        }
    },
    onBack() {
      this.$emit('previous-step');
    }
  }
}
</script>


<style>

strong{
width: 100%;

padding: 2%;
border-radius: 5px;
color: #fad819;
}

.itembtn{
  width: 100%;
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
  column-gap: 10px;

}
h2{
color: #fad819;

}
button{
width: 200px;
border: 0.5px solid #fad819;
background: none;
height: 30px;
color: #fad819;
cursor: pointer;
border-radius: 5px;
}

button:hover{
background: #fad819;
color: #000000;
}

.item {
width: 100%;
display: flex;
flex-direction: column;
align-content: center;
align-items: center;
}
.container{
font-family: 'Montserrat', sans-serif;
width: 100vw;
height: 100vh;
display: grid;
grid-template-columns: auto;
row-gap: 10%;
place-content: center;
}

.content{
max-width: 1424px;
width: 100vh;
display: grid;
grid-template-columns: 50% 50% ;
column-gap: 5%;

}



input{
width: 100%;
height: 40px;
background: none;
border-bottom: solid #fad8197e;
border-left: none;
border-right: none;
padding-left: 10px;
color: #fad819;
}
input::placeholder{
color: #fad819;
opacity: 0.4;
}

a {
  cursor: pointer;
  position: relative;
  display: inline-block;
  padding: 10px 20px;
  color: #fad819;
  font-size: 16px;
  text-decoration: none;
  text-transform: uppercase;
  overflow: hidden;
  transition: .5s;
  margin-top: 40px;
  letter-spacing: 4px
}

a:hover {
  background: #fad819;
  color: #000000;
  border-radius: 5px;
  box-shadow: 0 0 5px #ffed87,
              0 0 25px #fad819,
              0 0 50px #fad819,
              0 0 100px #ffed87;
}

 a span {
  position: absolute;
  display: block;
}

a span:nth-child(1) {
  top: 0;
  left: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #fad819);
  animation: btn-anim1 1s linear infinite;
}

@keyframes btn-anim1 {
  0% {
    left: -100%;
  }
  50%,100% {
    left: 100%;
  }
}

a span:nth-child(2) {
  top: -100%;
  right: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(180deg, transparent, #fad819);
  animation: btn-anim2 1s linear infinite;
  animation-delay: .25s
}

@keyframes btn-anim2 {
  0% {
    top: -100%;
  }
  50%,100% {
    top: 100%;
  }
}

 a span:nth-child(3) {
  bottom: 0;
  right: -100%;
  width: 100%;
  height: 2px;
  background: linear-gradient(270deg, transparent, #fad819);
  animation: btn-anim3 1s linear infinite;
  animation-delay: .5s
}

@keyframes btn-anim3 {
  0% {
    right: -100%;
  }
  50%,100% {
    right: 100%;
  }
}

 a span:nth-child(4) {
  bottom: -100%;
  left: 0;
  width: 2px;
  height: 100%;
  background: linear-gradient(360deg, transparent, #fad819);
  animation: btn-anim4 1s linear infinite;
  animation-delay: .75s
}

@keyframes btn-anim4 {
  0% {
    bottom: -100%;
  }
  50%,100% {
    bottom: 100%;
  }
}


</style>