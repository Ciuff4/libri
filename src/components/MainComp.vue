<template>
  <main class="container">
      <input class="form-control" type="text" v-model="autore" @keyup.enter="apiRequest">
      <BookComp
      v-for="book in books" :key="book.key"
      :titolo="book.title"
      :annoPubblicazione="book.first_publish_year"
      :editori="book.publisher"
      />
  </main>
</template>

<script>

import axios from 'axios';
import BookComp from './BookComp.vue';

export default {
name:'MainComp',
components:{
    BookComp
},

data(){
    return{
        apiUrl:'http://openlibrary.org/search.json',
        books:[],
        autore:''
    }
},

mounted(){
    this.apiRequest();
},

methods:{
    apiRequest(){
        axios.get(this.apiUrl,{
            params:{
                author: this.autore
            }
        })
        .then(result=>{
            this.books=result.data.docs;
            console.log(this.books);
        })
    },
}
}
</script>

<style>

</style>