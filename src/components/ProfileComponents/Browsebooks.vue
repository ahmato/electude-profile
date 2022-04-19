<template>
  <div>
    <div class="buttons">
      <button id="frofile-btn" class="Button" @click="renderProfileBooks">Profile</button>
      <button id="books-btn" class="Button" @click="renderBrowseBooks">Browse Books</button>
    </div>
    <bookElemnet :books="booksToDisplay" :userBooksArray="userBooksArray" @checkedBooks="checked_books" />
  </div>
</template>
<script>
import bookElemnet from '../../components/Helpers/Card-book.vue';
export default {
  name: 'Browse_books',
  props: ['books', 'userBooksArray'],
  components: {
    bookElemnet
  },
  data() {
    return {
      booksToDisplay: this.books,
      allBooks: this.books,
      displayAllBoooks: true,
      newBooksList: [],
      pageTitle: 'Browse Books'
    };
  },
  methods: {
    renderBrowseBooks() {
      this.booksToDisplay = this.allBooks;
    },
    renderProfileBooks() {
      this.booksToDisplay = this.getUserBooks();
    },
    getUserBooks() {
      let userBooks = [];
      this.newBooksList.forEach(userBookdId => {
        this.books.forEach(book => {
          if (book.id === userBookdId) {
            userBooks.push(book);
          }
        });
      });

      return userBooks;
    },
    checked_books(book_id) {
      this.newBooksList = book_id;
    }
  }
};
</script>
<style scoped>
button {
  border: none;
  background: none;
  outline: none;
  color: rgb(81, 85, 81);
  font-weight: bold;
  font-size: 1rem;
  margin: 0 20px;
  width: 10rem;
}
button:focus {
  outline: none;
  box-shadow: none;
  background: rgba(99, 233, 121, 0.3);
  color: rgb(22, 122, 22);
  border-radius: 6px;
}
.buttons{
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 10px ;
}
</style>
