<template>
    <div class="users-search">
            <div class="search-container">
                <h3>Search user</h3>
                <input :value="searchInpt" @input="searchUsers" :type="'text'" :placeholder="placeholderMssg" name="users-search" class="users-search d-block" id="users-search">
            </div>
        </div>
</template>
<script>
export default {
    name: 'UsersSearch',
    data(){
        return{
            searchInpt: '',
            placeholderMssg: 'Start Typing to find users'
        }
    },
    methods:{
        searchUsers(event){
            this.searchInpt = event.target.value;
            this.$emit('busqueda', this.searchInpt);
        }
    }
}
</script>
<style lang="scss">
    .users-search{
        display: block;
        width: 100%;
    }
    .search-container{
        width: 100%;
        max-width: 550px;
        @include marginAuto;
        text-align: left;
        margin-top: 50px;
        margin-bottom: 50px;
    }
</style>