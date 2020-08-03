<template>
  <div>
    <h1>Home</h1>
    <v-card class="mx-8">
      <v-data-table :headers="headers" :items="books" :items-per-page="20" class="elevation-1"></v-data-table>
    </v-card>
  </div>
</template>

<script>
import axios from "axios";

const BOOKS_URL = "https://drynyrd-bookshelf.builtwithdark.com/books";

export default {
  data: function() {
    return {
      headers: [{ text: "id", value: "id" }, { text: "name", value: "name" }],
      books: []
    };
  },
  methods: {
    fetchBooks: function() {
      axios.get(BOOKS_URL).then(response => (this.books = response.data));
    }
  },
  mounted: function() {
    this.fetchBooks();
  }
};
</script>

<style>
</style>
