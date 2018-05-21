<template>
 <div>
    <ul>
      <li v-for="(item,i) in article" :key='i'>
        <h2>{{ article[i].title.rendered }}</h2>
        <p v-html="article[i].excerpt.rendered"></p>
        <p>
          <span>{{ article[i].date }}</span>
        </p>
        <p>-------------------------------------------</p>
      </li>
    </ul>
 </div>
</template>
<script>
import axios from 'axios'
export default {
  data(){
    return {
        article:[],
    }
  },
  created(){
    this.getarticle()
  },
  methods: {
    getarticle(){
      axios.get('http://www.likecn.cn/wp-json/wp/v2/posts')
          .then(res=>{
              console.log(res.data);
              this.article =  res.data
          })
      }
    }
  }
</script>


<style>
</style>
