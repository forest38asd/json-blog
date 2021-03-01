<template>
  <div id="app">
      <PageNavigateComponent
              v-bind:pageNumber="pageNumber"
      />
      <Plate
            v-for="article of paginatedArticles"
            v-bind:article="article"
            v-bind:user="users.find(user => user.id === article.userId)"
            :key="article.id"
      />
  </div>
</template>

<script>
import Plate from "@/components/Plate";
import PageNavigateComponent from "@/components/PageNavigateComponent";
export default {
  name: 'App',
  components: {
      PageNavigateComponent,
      Plate
  },
  data() {
    return {
      articles: [],
      users: [],
        pageNumber: 0,
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/posts')
            .then((response) => response.json())
            .then(json => this.articles = json)
    fetch('https://jsonplaceholder.typicode.com/users')
            .then((response) => response.json())
            .then(json => this.users = json)
  },
  methods: {
      nextPage(){
          this.pageNumber++;
      },
      prevPage(){
           this.pageNumber--;
      },
      chosePage(page){
          this.pageNumber = page-1
      }
  },
    props: {
        size:{
            type:Number,
            required:false,
            default: 5
        },

    },
    computed: {
        pageCount(){
            let l = this.articles.length,
                s = this.size;
            return Math.ceil(l/s);
        },
        paginatedArticles(){
            const start = this.pageNumber * this.size,
                end = start + this.size;
            return this.articles.slice(start, end);
        }
    }
}
</script>

<style>
    #app {
      font-family: Avenir, Helvetica, Arial, sans-serif;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #2c3e50;
      margin-top: 0.5rem;
    }
</style>
