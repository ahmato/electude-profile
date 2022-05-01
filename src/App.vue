<template>
  <div id="app">
    <Navbar @targetPage="targetPage" />
    <div v-if="this.curretPage === 'editProfile'">
      <EditProfile :user="user" @editedUser="editedUser" />
    </div>
    <div>
      <TodoList />
    </div>
    <div v-if="this.curretPage === 'profile'">
      <ProfileView :user="user" :books="books" />
    </div>
  </div>
</template>
<script>
import ProfileView from './components/ProfileView.vue';
import Navbar from './components/Navbar.vue';
import EditProfile from './components/ProfileComponents/Edit-Profile.vue';
import TodoList from './components/Test-components/TodoList.vue'

export default {
  name: 'App',
  components: {
    ProfileView,
    Navbar,
    EditProfile,
    TodoList
  },
  data() {
    return {
      curretPage: 'profile',
      user: {
        full_name: 'Adam Smith',
        e_mail: 'Adam@gmail.com',
        password: '123456',
        user_BooksArray: [1, 5]
      },
      books: [
        { id: 1, name: 'The Russian', type: 'Fiction', available: true },
        { id: 2, name: 'Just as I Am', type: 'Non-fiction', available: false },
        { id: 3, name: 'The Vanishing Half', type: 'Fiction', available: true },
        { id: 4, name: 'The Midnight Library', type: 'Fiction', available: false },
        { id: 5, name: 'Untamed', type: 'Non-fiction', available: false },
        { id: 6, name: 'Viscount Who Loved Me', type: 'Fiction', available: true }
      ]
    };
  },
  methods: {
    targetPage(targetPage) {
      this.curretPage = targetPage;
    },
    editedUser(updatedUser) {
      (this.user.full_name = updatedUser.userName), (this.user.e_mail = updatedUser.email), (this.user.password = updatedUser.password);
    }
  }
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
