<template>
  <div id="app">
      <ProfileView :user="user"  />
  </div>
</template>
<script>
import ProfileView from './components/ProfileView.vue';

export default {
  name: 'App',
  components: {
    ProfileView,

  },
  data() {
    return {
      user: {
        full_name:'Adam Smith',
        e_mail: 'Adam@gmail.com',
        password:'123456',
      },
    };
  },
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
