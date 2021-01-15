<template>
  <div class="about">
    <h1>About me / About this project</h1>
    <div class="flex-container container">
      <div class="flex-item-about img-container">
        <img :src="img" alt="Daniel Verdú Martínez">
      </div>
      <div class="flex-item-about">
        <p>Hola!!<br> Mi nombre es Daniel Verdú Martínez y soy Desarrollador FrontEnd.</p>
        <p>Disfruto muchísimo creando diferentes proyectos personales como este, en el que puedo dejar volar mi imaginación, en este caso con la "excusa" de tener para este 2021 un alto conocimiento sobre VueJS.</p>
        <h3>Sobre el proyecto: </h3>
        <p>No es la primera vez que me encuentro con <span class="c-green">Vue</span> en el ambito profesional, aunque si es mi primer proyecto personal. En el he querido testear por mi mismo el uso de diferentes componentes y la comunicación entre ellos utilizando las <span class="c-green">props</span>, los <span class="c-green">$events</span> o el paso de data a través de los <span class="c-green">$route.$params</span>.</p>
        <p>Este es un pequeño proyecto pero el comienzo de algo grande!</p>
        <p>Espero que lo disfrutes.</p>
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
.flex-container{
  flex-direction: column;
}
.flex-item-about{
  width: 100%;
  display: block;
}
.img-container{
  margin-right: 0px;
  img{
    width: 100%;
    max-width: 450px;
  }
}
@media screen and(min-width: 1140px){
    .flex-container{
      flex-direction: row;
    }
    .flex-item-about{
      width: 50%;
    }
  }
</style>
