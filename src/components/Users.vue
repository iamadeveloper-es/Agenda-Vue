<template>
  <div class="users container">
      <div :class="{active: isActive}" class="alert-user-selected">
          {{ alertMssgSelected }}
      </div>
      <search-users @busqueda="search = $event"></search-users>
      <div class="search-counter" v-bind:search="search" v-if="search != 0 && searchUser.length != 0">
          <h3>We found: <span class="c-green">{{searchUser.length}}</span> results</h3>
      </div>
      <div class="no-results" v-if="searchUser.length == 0">
        <h2>{{noresultsMssg + ' ' + search}}</h2>
        <img width="150px" src="../assets/not-found.png" alt="">
      </div>      
        <div v-for="(user, index) in searchUser" :key="index" :id="user.id.value" class="user-container">
            <div class="user__header">
                <span class="ico far fa-heart"></span>
                <div class="user__img">
                    <img :src="user.picture.large" alt="">
                </div>
            </div>
            <div class="user__body">
                <h3 class="user__title"><span class="d-block">Hi, My name is</span>{{user.name.first + ' ' + user.name.last}}</h3>
            </div>
            <div class="user__footer">
                <button @click="addUser(index, user)" class="btn--custom shadow white">Add to contacts</button>
                <span class="ico fas fa-globe-americas"></span>
                <span>{{ user.location.country }}</span>
            </div>
      </div> 
  </div>
</template>

<script>
import SearchUsers from './SearchUsers.vue';

export default {
  components: { SearchUsers },
    name: 'Users',

    data(){
        return{
            url : 'https://randomuser.me/api/?',
            people: 'results=20',
            users: [],
            search: '',
            noresultsMssg: 'No hay reulstados para',
            usersSelected: [],
            alertMssgSelected: 'is added to you contacts!',
            isActive: false
        }
    },
    created() {
        this.axios.get(this.url + this.people).then((response) => {
            this.renderUsers(response);
            
        })
    },
    methods: {
        renderUsers(response){
            this.users = response.data.results;
            console.log(this.users = response.data.results);
        },
        saveUser(event){
            this.userSelected = event;
            console.log(event.target);
            this.$emit('saveUsers', this.userSelected);
        },
        addUser(index, user){
            this.isActive = true;
            setTimeout(() => {
                this.isActive = false;
            }, 2500);
            this.usersSelected.splice(index, 1, user);
            console.log(this.usersSelected);
            this.$emit('passUsers', this.usersSelected);
        }
    },
    computed: {
        searchUser(){
            return this.users.filter((user) => {
                return user.name.first.toLowerCase().match(this.search.toLowerCase());              
                
            })
        }
    }
}

</script>

<style lang="scss">
.alert-user-selected{
    position: fixed;
    bottom: 0;
    transform: translateY(100%);
    left: 0;
    right: 0;
    z-index: 99;
    padding: 20px 0;
    background-color: $darkBlue;
    color: $white;
    &.active{
       /* top: inherit;
        bottom: 0; */
        animation: fade-up 2.5s ease-in-out 1;
        
    }

}
@keyframes fade-up{
    0%{
        transform: translateY(100%);
    }
    25%{
        transform: translateY(0%);
    }
    50%{
        transform: translateY(0%);
    }
    100%{
        transform: translateY(100%);
    }
}
.search-counter{
    text-align: center;
    display: block;
    width: 100%;
}
 .users{
        display: flex;
        align-items: middle;
        flex-wrap: wrap;
        justify-content: center;
        .ico{
            display: block;
        }
        .user-container{
            width: calc(100%);
            margin: 20px;
            height: auto;
            border-radius: $regularRadius;
            border: 1px solid $lightGrey;
            overflow: hidden;
            box-shadow: $boxShadow;
            background-color: $white;
            padding: 16px;
            color: $darkBlue;
            position: relative;
            &::before{
                content: '';
                position: absolute;
                bottom: 16px;
                left: 16px;
                width: calc(100% - 32px);
                height: 65%;
                background-color: $lightBlue;
            }

        }
        .user__header{
            background-color: $white;
            position: relative;
            &::before{
                content: '';
                position: absolute;
                bottom: 0;
                left: 0;
                width: 100%;
                height: 35%;
                background-color: $lightBlue;
            }
            .ico{
                text-align: left;
            }
        }
        .user__img{
            overflow: hidden;
            width: 160px;
            height: 160px;
            @include marginAuto;
            border-radius: $roundRadius;
            position: relative;
            border: 1px solid $lightGrey;
            img{
                width: 100%;
            }
        }
        .user__header, .user__body, .user__footer{
            position: relative;
            z-index: 20;
        }
        .user__body, .user__footer{
            background-color: $lightBlue;
        }
        .user__footer{
                margin-bottom: 25px;
            .ico{
                margin-top: 25px;
                text-align: center;
            }
        }
        .user__title{
            font-size: 22px;
            span{
                font-size: 16px;
            }
        }
    }
@media screen and(min-width: 758px){
    .users{
        .user-container{
            width: calc(100% / 2);
            max-width: 40%;
        }
        .user__img{
            max-height: 300px;
        }
    }
}
@media screen and(min-width: 991px){
    .users{
        .user-container{
            width: calc(100% / 3);
            max-width: 30%;
            height: 480px;
        }
    }
}
@media screen and(min-width: 1440px){
    .users{
        .user-container{
            width: calc(100% / 4);
            max-width: 20%;
        }
    }
}
</style>