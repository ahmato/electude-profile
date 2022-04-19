<template>
  <div class="header-box">
    <div class="container flex">
      <div class="profile-img">
        <img alt="Vue logo" class="imgPreview" src="../../assets/logo.png" />
      </div>
      <ul class="profileInfo">
        <li>Name: {{ user.full_name }} </li>
        <li>Email: {{ user.e_mail }}</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  props: ['user'],
  name: 'user-Profile'
};
</script>
<style scoped>
.header-box {
  width: 100%;
  border-bottom-style: solid;
  border-bottom-color: green;
}
.profile-img {
  float: left;
  border-style: solid;
  border-radius: 50%;
  margin: 10px 0 10px 10px;
}
.imgPreview {
  height: 80px;
  border-radius: 50%;
}
.profileInfo {
  height: 50px;
  float: right;
  width: 20rem;
}
.flex {
  display: flex;
}
ul {
  list-style-type: none;
}
li {
  padding-top: 5px;
}
</style>
