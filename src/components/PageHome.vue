<template>
  <b-container class="bv-example-row">
    <b-row class="row article" v-for="(article, index) in articles" :key="index">
      <b-col sm="12" lg="3" md="3"><b-img :src="'http://d8jsonapiapp.lndo.site' + included[index].attributes.uri.url" fluid alt="Responsive image"></b-img></b-col>
      <b-col sm="12" md="9" lg="9">
        <h1 class="title"> {{ article.attributes.title }} </h1>
        <div class="body" v-html="article.attributes.body.value">
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'HelloWorld',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        articles: {},
        included: {}
      }
    },
    mounted () {
      const inst = this
      axios.get('http://d8jsonapiapp.lndo.site/jsonapi/node/article?include=field_image', {
        headers: {
          'Accept': 'application/vnd.api+json'
        }
      }).then(function (result) {
        inst.articles = result.data.data
        inst.included = result.data.included
      })
    },
    methods: {}
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .row.article {
    transition: all 0.2s;
    margin-bottom: 1em;
    box-shadow: 0px 0px 10px lightblue;
    padding: 1em;
  }
  .row.article:hover {
    background: lightblue;
    color: white;
  }
  .row.article:hover img {
    transform: rotate3d(0, 20, 1, 12deg);
  }
</style>
