<template>
  <div class="home">
    <title-component></title-component>
    <button class="btn--custom shadow blue" @click="shareData()">Your Contacts</button>
    <span v-if="usuarios.length" class="counter">{{counter()}}</span>
    <p v-if="noUsers">You didn't save any user yet!</p>
    <Users @passUsers="usuarios = $event"/>
  </div>
</template>

<script>
import Users from '@/components/Users.vue';
import TitleComponent from '../components/TitleComponent.vue';

export default {
  name: 'Home',
  components: {
    Users,
    TitleComponent
  },
  data(){
    return{
      usuarios: [],
      noUsers: false
    }
  },
  methods:{
    shareData(){
      if(this.usuarios.length > 0){
        this.noUsers = false;
        this.$router.push({name: "Contacts", params:{data:this.usuarios}});
      }else{
        this.noUsers = true;
        setTimeout(() => {
          this.noUsers = false;
        }, 3000);
        console.log('no hay usuarios');
      }
      
    },
    counter(){
      if(this.usuarios.length > 0){
        let realUsers = [...new Set(this.usuarios)];
        return realUsers.length
      }
    }
  },
  computed:{
    usersLenght(){
      return console.log(this.Users.length);
    }
  }
}
</script>
<style lang="scss">
.number{
  opacity: 0;
}
  .counter{
    position: relative;
    display: inline-block;
    border-radius: $roundRadius;
    background-color: $lightBlue;
    padding: 5px;
    transform: translateX(10px);
    height: 32px;
    width: 32px;
  }
</style>
