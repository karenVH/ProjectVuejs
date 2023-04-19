<template>
  <div class="container">
    <div class="item">

      <h2>PASO {{ step }}</h2>
      <strong>{{ error }}</strong>
    </div>
    <div class="content">
      <input type="text" v-model="nombre" placeholder="Email">
      <input type="email" v-model="email" placeholder="Contraseña">
          <input type="password" placeholder="CONFIRMAR CONTRASEÑA" >
          <input type="number" placeholder="NUMERO TELEFONO" >
          <input type="number" placeholder="NUMERO CELULAR" >
        
      </div>
      <div class="itembtn">
        <button @click="onSubmit">SIGUIENTE</button>
        <button  @click="onBack">ANTERIOR</button>
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
border: 1px solid #fad819;
padding: 2%;
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




</style>