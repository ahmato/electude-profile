<template>
  <div id="app">
    <Navbar @targetPage="targetPage" />
    <ProfileView :user="user" />
  </div>
</template>
<script>
import ProfileView from './components/ProfileView.vue';
import Navbar from './components/Navbar.vue';

export default {
  name: 'App',
  components: {
    ProfileView,
    Navbar
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
