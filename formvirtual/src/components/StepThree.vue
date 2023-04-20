<template>
    <div class="container">
      <div class="item">

        <h2>PASO {{ step }}</h2>
        <strong>{{ error }}</strong>
      </div>
      <div class="content">
        <input type="text" v-model="direccion" placeholder="Direccion">
        <input type="email" v-model="codigopostal" placeholder="Codigo postal">
   
        </div>
        <div class="itembtn">
          
        <a @click="onSubmit">
      <span></span>
      <span></span>
      <span></span>
      <span></span>
      ENVIAR
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
  export default {
    props: {
      step: Number
    },
    data() {
      return {
        direccion: '',
        codigopostal: '',
        error: null
      }
    },
    methods: {
      onSubmit() {
        if (!this.direccion || !this.codigopostal) {
          this.error = 'Por favor, completa todos los campos';
        } else {
          this.error = null;
          this.$emit('next-step', { direccion: this.direccion, codigopostal: this.codigopostal });
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
  padding: 1%;
  border-radius: 5px;
  color: #fad819;
}

.itembtn{
  width: 100%;
  display: flex;
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
 display: grid;
 grid-template-columns: 50% 50%;

 column-gap: 5%;
 row-gap: 5%;
 place-content: center;
}

@media (max-width: 650px) {
  .content{
   display: grid;
 grid-template-columns: 90%;
 column-gap: 5%;
 row-gap: 5%;
 place-content: center;
}

}
.file-select::before {
  background-color: #fad819;
  background-image: url("../assets/galeria.svg");
  background-repeat: no-repeat;
  width: 100%;
  height: 40px;
  color: #000000;
  font-weight: 900;
  display: grid;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  border-bottom: none;
  border-radius: 10px;
  content: "SELECCIONAR IMAGE"; /* testo por defecto */
}
.file-select input[type="file"] {
  opacity: 0;
  width: 200px;
  height: 32px;
  display: inline-block;
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

select{
  width: 100%;
  height: 40px;
  background: none;
  border-bottom: solid #fad8197e;
  border-left: none;
  border-right: none;
  border-top: none;
  padding-left: 10px;
  color: #fad8197e;
}
select option{
background: #212121;
color: #bda521;
}
select option:hover{
  background: #181717;
color: #bda521;
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