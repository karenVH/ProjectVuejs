
<template>
  <!--
    
  --><div class="container">
    <div class="lbl-menu">
      <label for="radio1"> 1</label>
      <label for="radio2"> 2</label>
      <label for="radio3"> 3</label>
    </div>

    <form name="form" id="form" v-on:submit.prevent="procesar();">
      <div class="content">

        <input type="radio" name="radio" id="radio1" checked>
        <div class="tab1">
          <input type="text" id="name" placeholder="PRIMER NOMBRE" v-model="part1.primerNombre" >
          <input type="text" placeholder="SEGUNDO NOMBRE" v-model="part1.segundoNombre" >
          <select name="" id="myDiv" >
            <option value="" >PAIS</option>
          </select>
          <input type="date" placeholder="FECHA" v-model="part1.fecha" >
          <select name="" id="" v-model="part1.tipoDocumento" value="TIPO DOCUMENTO" >
            <option value="" >TARJETA IDENTIDAD</option>
            <option value="">CÉDULA</option>
            <option value="">PASAPORTE</option>
          </select>
          <input type="number" placeholder="NUMERO DE DOCUMENTO" v-model="part1.numeroDocumento" >
          <input type="file" placeholder="FOTO DOCUMENTO ADELANTE" @change="onChangeFile" class="file-select">
          <input type="file" placeholder="FOTO DOCUMENTO ATRÁS" @change="onChangeFile2" class="file-select">
        
        </div>

        <input type="radio" name="radio" id="radio2">
        <div class="tab2">
          <!-- paso 2 -->

          <input type="text" placeholder="EMAIL" v-model="part2.email">
          <input type="password" placeholder="PASSWORD" v-model="part2.password">
          <input type="password" placeholder="CONFIRMAR CONTRASEÑA" v-model="part2.passwordConfirm">
          <input type="number" placeholder="NUMERO TELEFONO" v-model="part2.tel">
          <input type="number" placeholder="NUMERO CELULAR" v-model="part2.phone">
        
        </div>

        <input type="radio" name="radio" id="radio3">
        <div class="tab3">

        <!-- paso 3 -->
        <input type="text" placeholder="DIRECCION RESIDENCIA" v-model="part3.addres">
        <input type="number" placeholder="CODIGO POSTAL" v-model="part3.codigoPostal">
        <input type="submit" value="ENVIAR" title="Enviar" class="button" />
        </div>
      </div>
    </form>
  </div>

  <div class="container">

        
    </div>
</template>

<script>

export default {
  name: 'ContactoComponent',
  data() {
    return {
      part1: {
        primerNombre: "",
        segundoNombre: "",
        pais: "",
        genero: "",
        fecha: "",
        tipoDocumento: "",
        numeroDocumento: "",
        fotoAdelante: "",
        fotoAtras: ""
      },
      part2: {
        email: "",
        password: "",
        passwordConfirm: "",
        tel: "",
        phone: ""
      },
      part3: {
        addres: "",
        codigoPostal: ""
      },
    }
  },
  methods: {
    procesar() {
     alert("has sido registrado con estos datos: \n" + "Primer nombre" + this.part1.primerNombre + "\n" +  "segundo nombre" + this.part1.segundoNombre + "\n" + "pais" + this.part1.pais + "\n"  + "Fecha" + this.part1.fecha + "\n" + "tipo documento" + this.part1.tipoDocumento + "\n"  + "Numero documento" + this.part1.numeroDocumento + "\n" + "Foto adelante" + this.part1.fotoAdelante + "\n" + "foto atras" + this.part1.fotoAtras + "\n" + "Email" + this.part2.email + "\n" + "Contraseña" + this.part2.password + "\n"  + "Telefono" + this.part2.tel + "\n" + "Numero Celulat" + this.part2.phone + "\n" + "Direccion" + this.part3.addres + "\n" + "Codigo postal" + this.part3.codigoPostal)
    },
    onChangeFile(event) {
      this.$emit('update:modelValue', event.target.files[0])
    },
    onChangeFile2(event) {
      this.$emit('update:modelValue', event.target.files[0])
    }
  }
}

//peticion para los paises
//validacion de formulario

</script>

<style scoped>
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
  border-radius: 5%;
  content: "SELECCIONAR IMAGE"; /* testo por defecto */
}

.file-select input[type="file"] {
  opacity: 0;
  width: 200px;
  height: 32px;
  display: inline-block;
}

.container{
    width: 100%;
   display: flex;
   flex-direction: column;
   padding-right: 50px;
   font-family: 'Montserrat', sans-serif;

}
.lbl-menu{
    width: 100%;
    display: grid;
    grid-template-columns: 30% 30% 30%;
    column-gap: 20px;
}
.lbl-menu label{
    display: flex;
    justify-content: center;
    align-content: center;
    align-items: center;
    padding: 5px;
    width: 30px;
    height: 30px;
    background: #fad819;
    color: #000000;
    cursor: pointer;
    transition: all 400ms ease;
    border-radius: 50%;
    font-weight: 800;
}
.lbl-menu label:hover{
    background: #bda521;
}
.content{
  position: relative;
}
.content div{
    width: 800px;
    height: 400px;
    position: absolute;
    right: -130%;
    line-height: 1.8;
    transition: all 600ms ease;
    opacity: 0;
    visibility: hidden;
    transform: scale(0.90);
    background: none;
}
#radio1,#radio2,#radio3{
    display: none;
}
#radio1:checked ~ .tab1,
#radio2:checked ~ .tab2,
#radio3:checked ~ .tab3
{
    opacity: 1;
    visibility: visible;
    transform: scale(1);
}
.content div:after{
    position: absolute;
    content: "";
    border-left: 10px solid transparent;
    border-right: 10px solid transparent;
    border-top: 10px solid transparent;

    bottom: 100%;
    left: 28px;
}
.content .tab2:after{
    left: 12px;
}
.content .tab3:after{
    left: 110px;
}

.tab1{
  width: 100%;
  display: grid;
  place-content: center;
  grid-template-columns: 320px 320px;
  column-gap: 30px;
  row-gap: 30px;
}

.tab2{
  width: 100%;
  display: grid;
  place-content: center;
  grid-template-columns: 320px 320px;
  column-gap: 30px;
  row-gap: 30px;
}

.tab3{
  width: 100%;
  display: grid;
  place-content: center;
  grid-template-columns: 320px 320px;
  column-gap: 30px;
  row-gap: 30px;
}

@media (max-width: 800px) {
  .tab1{
    margin-top: 160px;
  width: 100%;
  display: grid;
  place-content: center;
  grid-template-columns: 320px;
  row-gap: 50px;
}

.tab2{
  margin-top: 30px;
  width: 100%;
  display: grid;
  place-content: center;
  grid-template-columns: 320px;
  row-gap: 50px;
}

.tab3{
  width: 100%;
  display: grid;
  place-content: center;
  grid-template-columns: 320px;
  row-gap: 50px;
}
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

.button{
  font-weight: 800;
  border-radius: 4px;
  cursor: pointer;
  border: solid #fad819;
  background: none;
  color: #fad819;
}

.button:hover{
  background: #fad819;
  color: #212121;
  border: none;
}
</style>