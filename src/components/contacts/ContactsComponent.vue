<template>
  <div class="contacts">
    <h1>Contacts</h1>
    <h2 v-if="addedUsers == undefined">Yo Don't have any contact yet!</h2>
    <div v-else>
      <p>You actually have {{addedUsers.length}} contacts</p>
    <ul>
      <li v-for="(user, index) in addedUsers" :key="index">
        <div class="contacts__user flex-container">
          <div class="flex-item">
            <div class="user__img">
              <img :src="user.picture.large" alt="">
            </div>            
          </div>
          <div class="flex-item user__name">
            {{ user.name.first + ' ' + user.name.last}}
          </div>
          <div class="flex-item user__info">
            <span class="ico fas fa-phone-square"></span>
            {{ user.phone}}
          </div>
        </div>
      </li>
    </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CotactsComponent',
  props: ['users'],
    data(){
        return{
            addedUsers: null
        }
    },
    created(){
      this.addedUsers = this.users
    }

}
</script>

<style lang="scss">
ul{
  padding-left: 0;
}
  li{
    list-style: none;
    background-color: $lightBlue;
    padding: 15px;
    margin-bottom: 5px;
  }
  .flex-container{
        flex-direction: column;
  }
  .flex-item{
    width: calc(100% / 3);
    margin: 0 10px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .user__img{
      overflow: hidden;
      width: 80px;
      height: 80px;
      border-radius: $roundRadius;
      @include marginAuto;
      position: relative;
      border: 1px solid $lightGrey;
      img{
                width: 100%;
      }
  }
  .user__info{
    .ico{
      margin-right: 15px;
    }
  }
  @media screen and(min-width: 758px){
    .flex-container{
      flex-direction: row;
    }
  }
</style>