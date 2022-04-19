<template>
  <div class="list-group">
    <ul v-for="book in books" :key="book.id">
      <li>
        <label for="title">Title: </label>
        <span class="title">{{ book.name }}</span>
      </li>
      <li>
        <label for="type">Type: </label>
        <span> {{ book.type }} </span>
      </li>
      <li>
        <label for="available">Available: </label>
        <span> {{ getAvailabilityMessage(book.available) }} </span>
      </li>
      <li class="checkbox">
        <input type="checkbox" v-model="userCheckedBooks" :id="book.id" :value="book.id" />
        {{ getCheckboxText(book.id) }}
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'Profile_books',
  props: ['books', 'userBooksArray'],
  data() {
    return {
      userCheckedBooks: []
    };
  },
  watch: {
    userCheckedBooks() {
      this.$emit('checkedBooks', this.userCheckedBooks);
    }
  },
  mounted() {
    this.userCheckedBooks = this.userBooksArray;
  },
  methods: {
    getAvailabilityMessage(status) {
      if (status === true) {
        return 'Yes';
      } else {
        return 'No';
      }
    },
    getCheckboxText(bookId) {
      let text = 'Add';
      this.userCheckedBooks.forEach(userBookId => {
        if (bookId === userBookId) {
          text = 'Remove';
        }
      });
      return text;
    }
  }
};
</script>
<style scoped>
ul {
  list-style-type: none;
  background-color: #ffffff;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);
  border-bottom: 1px solid #ccc;
  font-size: 16px;
  max-width: 30rem;
  margin: 1.5rem auto;
  padding: 1rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
}
li {
  padding: 5px;
}
input {
  padding-top: 15px;
}
.title {
  font-weight: bold;
  font-size: 1rem;
}
label {
  color: rgba(0, 0, 0, 0.658);
}
/* .checkbox {
  color: black !important;
} */
</style>
