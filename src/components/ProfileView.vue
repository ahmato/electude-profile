<template>
  <div>
    <Profile :user="user"  />
  </div>
</template>
<script>
import Profile from '../components/ProfileComponents/Profile.vue';

export default {
  name: 'ProfileView',
  props: ['user'],
  components: {
    Profile,
  },
};
</script>

