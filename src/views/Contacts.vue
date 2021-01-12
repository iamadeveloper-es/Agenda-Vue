<template>
  <div class="contacts">
      <contacts-component :users="myUsers"></contacts-component>
  </div>
</template>

<script>
import ContactsComponent from '../components/contacts/ContactsComponent.vue'
export default {
  name: 'Contacts',
  components: { ContactsComponent },
  data(){
    return{
      myUsers: null
    }
  },
  created(){
    this.myUsers = this.$route.params.data
  }


}
</script>

<style>

</style>