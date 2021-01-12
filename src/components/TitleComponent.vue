<template>
  <div class="title-component">
      <div class="img__container">
            <img class="logo" :src="img" alt="">
      </div>
      <div class="title-container">
            <h1>{{title}}</h1>
            <h2>Make a contact agenda using Random User API</h2> 
      </div>
      
  </div>
</template>

<script>
export default {
    name: 'TitleComponent',
    data(){
        return{
            title: 'Agenda with Vuejs',
            img: require('../assets/hombre.png') 
        }
    }
}
</script>

<style lang="scss">
    .title-component{
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        .img__container{
            margin-right: 25px;
        }
        .logo{
            width: 100px;
        }
    }

    @media screen and(min-width: 758px){
        .title-component{
            flex-direction: row;
            .title-container{
            text-align: left;
        }
        }
    }
</style>