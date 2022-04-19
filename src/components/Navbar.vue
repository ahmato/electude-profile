<template>
  <div class="title-box">
    <div class="editProfile">
      <button @click="onProfile">Profile</button>
      <button @click="onEditeProfile">Edit Profile</button>
      <h4>{{ pageTitle }}</h4>
    </div>
  </div>
</template>
<script>
export default {
  name: 'pageTitle',
  data() {
    return {
      pageTitle: 'Profile'
    };
  },
  methods: {
    onEditeProfile() {
      this.pageTitle = 'Edit Profile';
      this.$emit('targetPage', 'editProfile');
    },
    onProfile() {
      this.pageTitle = 'Profile';
      this.$emit('targetPage', 'profile');
    }
  }
};
</script>

<style scoped>
.title-box {
  background-color: green;
  margin: 0;
  padding: 0;
  color: rgb(255, 255, 255);
  height: 4rem;
}
h4 {
  margin-left: 20rem;
  padding: 15px;
  display: inline;
  text-align: center;
  justify-content: center;
  align-items: center;
}
.editProfile {
  float: left;
}
button {
  border: 1px solid #521751;
  color: white;
  cursor: pointer;
  border-radius: 6px;
  font-size: 0.8rem;
  margin: 10px;
  width: 5rem;
  height: 1.5rem;
  background: rgba(216, 243, 220, 0.164);
  border: none;
  background: none;
  text-decoration: underline;
  background-color: green !important;
  padding: 0 !important;
}
</style>
