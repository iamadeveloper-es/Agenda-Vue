<template>
  <div class="about">
    <h1>About me / About this project</h1>
    <div class="flex-container container">
      <div class="flex-item img-container">
        <img :src="img" alt="Daniel Verdú Martínez">
      </div>
      <div class="flex-item">
        <p>Hola!!<br> Mi nombre es Daniel Verdú Martínez y soy Desarrollador FrontEnd.</p>
        <p>Disfruto muchísimo creando diferentes proyectos personales como este en el que puedo dejar volar mi imaginación, en este caso con la "excusa" de querer para este 2021 tener un alto conocimiento sobre VueJS</p>
        <h3>Sobre el proyecto: </h3>
        <p>Este es mi primer proyecto personal desarrollado con <span class="c-green">Vue-cli</span>, pero no el primero en el ambito laboral. En el quería plasmar el uso de diferentes componentes y la comunicación entre ellos utilizando las <span class="c-green">props</span>, los <span class="c-green">$events</span> o el paso de data a través de los <span class="c-green">$route.$params</span></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'About',
    data(){
      return{
        img: require('../assets/me.jpg') 
      }
    }
}
</script>

<style lang="scss">
.about{
  p{
    font-size: 22px;
    text-align: left;
  }
  h3{
    text-align: left;
  }
}
.flex-item{
  width: 50%;
  display: block;
}
.img-container{
  margin-right: 0px;
  width: 40%;
  img{
    width: 100%;
    max-width: 450px;
  }
}
</style>
