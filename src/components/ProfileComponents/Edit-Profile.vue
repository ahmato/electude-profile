<template>
  <div class="root">
    <h2>Edite Profile</h2>
    <form @submit.prevent>
      <p>
        <input type="text" :placeholder="user.full_name" v-model="state.fullName" />
        <span v-if="v$.fullName.$error">
          {{ v$.fullName.$errors[0].$message }}
        </span>
      </p>
      <p>
        <input type="text" :placeholder="user.e_mail" v-model="state.email" />
        <span v-if="v$.email.$error">
          {{ v$.email.$errors[0].$message }}
        </span>
      </p>
      <p>
        <input type="password" placeholder="Password" v-model="state.password.password" />
        <span v-if="v$.password.password.$error">
          {{ v$.password.password.$errors[0].$message }}
        </span>
      </p>
      <p>
        <input type="password" placeholder="Confirm Password" v-model="state.password.confirm" />
        <span v-if="v$.password.confirm.$error">
          {{ v$.password.confirm.$errors[0].$message }}
        </span>
      </p>
      <button @click="submitForm">Submit</button>
    </form>
  </div>
</template>
<script>
import useValidate from '@vuelidate/core';
import { email, minLength, sameAs } from '@vuelidate/validators';
import { reactive, computed } from 'vue';

export default {
  name: 'EditProfile',
  props: ['user'],
  setup() {
    const state = reactive({
      fullName: '',
      email: '',
      password: {
        password: '',
        confirm: ''
      }
    });

    const rules = computed(() => {
      return {
        fullName: { minLength: minLength(8) },
        email: { email },
        password: {
          password: { minLength: minLength(6) },
          confirm: { sameAs: sameAs(state.password.password) }
        }
      };
    });

    const v$ = useValidate(rules, state);

    return {
      state,
      v$
    };
  },
  methods: {
    submitForm() {
      this.v$.$validate();

      if (!this.v$.$error) {
        const editedUser = {
          userName: this.state.fullName ? this.state.fullName : this.user.full_name,
          email: this.state.email ? this.state.email : this.user.e_mail,
          password: this.state.password.password ? this.state.password.password : this.user.password
        };
        this.$emit('editedUser', editedUser);
      }
    }
  }
};
</script>

<style lang="css" scoped>
.root {
  width: 400px;
  margin: 0 auto;
  background-color: #fff;
  padding: 30px;
  margin-top: 100px;
  border-radius: 20px;
}

input {
  border: none;
  outline: none;
  border-bottom: 1px solid #ddd;
  font-size: 1em;
  padding: 5px 0;
  margin: 10px 0 5px 0;
  width: 100%;
}

button {
  background: rgba(62, 128, 72, 0.596);
  padding: 10px 20px;
  margin-top: 10px;
  border: none;
  color: white;
}
button {
  border: 1px solid #521751;
  color: #000000;
  cursor: pointer;
  border-radius: 6px;
  font-weight: bold;
  font-size: 1rem;
  margin: 10px;
  width: 10rem;
  height: 2rem;
  background: rgba(62, 128, 72, 0.596);
}
span {
  color: red;
}
</style>
