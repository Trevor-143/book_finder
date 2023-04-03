<template>
  <div class="nav">
    <h3>book<span>FINDER</span></h3>
    <form @submit.prevent="findBook()" >
      <input type="text" v-model="lookText" placeholder="e.g excellence..">
      <input type="submit" value="Search" >
    </form>
  </div>

  <div class="showRoom">
    <div class="showRoomBook" v-for="book in showBooks" :key="book.id">
      <router-link to="/about">
        <img :src="book.published_works[0].cover_art_url" :alt="book.title">
      </router-link>
      <div class="bookMini">
        <h3 class="title">{{ book.title }}</h3>
        <h3 class="author">{{ book.authors[0] }}</h3>
      </div>
  </div>

  <div class="notShowAbout">
      <mainFooter value="title" />
    </div>
  </div>

  

</template>

<script>
import { ref, onBeforeMount } from "vue"
import mainFooter from "@/components/mainFooter";

export default {

  name: 'HomeView',
  components: {
    mainFooter
  },

  setup() {
    const showBooks = ref([])
    const lookText = ref('')
    const options = {
      method: 'GET',
      headers: {
        'X-RapidAPI-Key': 'f6dd938eacmsh0d384b1080b54fbp10dd7cjsn5485a7bd7a65',
        'X-RapidAPI-Host': 'book-finder1.p.rapidapi.com'
      }
    }

    const findBook = () => {
      fetch(`https://book-finder1.p.rapidapi.com/api/search?title=${lookText.value}&results_per_page=100`, options)
      .then(resp => resp.json())
      .then(data => {
        showBooks.value = data.results
        console.log(showBooks.value)
      })
      lookText.value = null
    }


    onBeforeMount(() => {
      fetch(`https://book-finder1.p.rapidapi.com/api/search?title=excellence&results_per_page=100`, options)
      .then(res => res.json())
      .then(data => {
        showBooks.value = data.results
        console.log(showBooks.value)
      })
    })
    
    return {
      showBooks,
      lookText,
      findBook
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

.now {
  background-color: #000;
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 1rem;
}
.nav h3 {
  background-color: #000;
  color: #fff;
  padding: 10px 13px;
  border-radius: 10px;
}
.nav h3 span {
  background-color: #fff;
  color: #000;
  padding: 5px 10px;
  border-radius: 10px;
  margin-left: 10px;
}
.nav form input:focus {
  outline: none;
  background-color: none;
}
.nav form input[type=text] {
  padding: 10px 15px;
  border: none;
  background-color: #000000;
  color: #ffffff;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
}
.nav form input::placeholder {
  color: #fff;
}
.nav form input[type=submit] {
  background-color: #000;
  color: #fff;
  border: none;
  padding: 10px 15px;
  cursor: pointer;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  border-left: #fff 3px solid;
}

.showRoom {
  margin-top: 3rem;
  margin-bottom: 2rem;
  display: grid;
  gap: 2rem;
  grid-template-columns: repeat(auto-fit, minmax(10rem, 1fr));
  cursor: pointer;
}

.showRoomBook img {
  width: 100%;
  border-radius: 10px;
  transition: 0.4s;
  min-height: 270px;
}
.showRoomBook img:hover {
  box-shadow: -1px 15px 32px 4px rgba(0,0,0,0.24);
  -webkit-box-shadow: -1px 15px 32px 4px rgba(0,0,0,0.24);
  -moz-box-shadow: -1px 15px 32px 4px rgba(0,0,0,0.24);
  transform: translateY(-20px);
}

.title {
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2; /* number of lines to show */
          line-clamp: 2; 
  -webkit-box-orient: vertical;
  font-size: 15px;
}
.author {
  font-size: 13px;
  color: #6b6b6b;
}
/* .notShowAbout {
  display: none;
} */
</style>
