<template>
    <div class="container">
      <div class="item">

        <h2>PASO {{ step }}</h2>
        <strong>{{ error }}</strong>
      </div>
      <div class="content">
        <input type="text" v-model="nombre" placeholder="nombre">
        <input type="email" v-model="email" placeholder="email">
      <select name="" id="">
        <option value="">País</option>
      </select>   
          <select name="" id="">
            <option value="">Genero</option>
            <option value="">mujer</option>
              <option value="">hombre</option>
          </select>
          <input type="text" name="fname" placeholder="First Name" />
          <input type="text" name="lname" placeholder="Last Name" />
          <input type="text" name="phone" placeholder="Phone" />
          <input type="date">
          <select name="" id="">
            <option value="">CC</option>
            <option value="">TI</option>
            <option value="">PP</option>
          </select>
          <input type="number" placeholder="Numero documento"/>
          <input type="file" placeholder="FOTO DOCUMENTO ADELANTE" class="file-select">
          <input type="file" placeholder="FOTO DOCUMENTO ATRÁS" class="file-select">
        
        </div>
        <div class="item">

          <button @click="onSubmit">SIGUIENTE</button>
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
        nombre: '',
        email: '',
        error: null
      }
    },
    methods: {
      onSubmit() {
        if (!this.nombre || !this.email) {
          this.error = 'Por favor, completa todos los campos';
        } else {
          this.error = null;
          this.$emit('next-step', { nombre: this.nombre, email: this.email });
        }
      }
    }
  }
  </script>


<style>

strong{
  width: 100%;
 border: 1px solid #fad819;
  padding: 2%;
  border-radius: 5px;
  color: #fad819;
}

.errordiv img{
  width: 50px;
  height: 50px;
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


</style>