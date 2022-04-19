<template>
  <div>
    <Profile :user="user"/>
    <BrowseBooks :books="books" :userBooksArray="user.user_BooksArray" />
  </div>
</template>
<script>
import Profile from '../components/ProfileComponents/Profile.vue';
import BrowseBooks from './ProfileComponents/Browsebooks.vue';

export default {
  name: 'ProfileView',
  props: ['user','books'],
  components: {
    Profile,
    BrowseBooks
  },
};
</script>

