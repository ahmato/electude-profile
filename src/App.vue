<template>
  <div id="app">
    <Navbar @targetPage="targetPage"/>
    <div v-if="this.curretPage === 'editProfile'">
      <EditProfile  :user="user"/>
    </div>
    <div v-if="this.curretPage === 'profile'">
      <ProfileView :user="user"/>
    </div>
  </div>
</template>
<script>
import ProfileView from './components/ProfileView.vue';
import Navbar from './components/Navbar.vue';
import EditProfile from './components/ProfileComponents/Edit-Profile.vue'

export default {
  name: 'App',
  components: {
    ProfileView,
    Navbar,
    EditProfile
  },
  data() {
    return {
      curretPage: 'profile',
      user: {
        full_name: 'Adam Smith',
        e_mail: 'Adam@gmail.com',
        password: '123456'
      }
    };
  },
  methods: {
    targetPage(targetPage) {
      this.curretPage = targetPage;
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
