<template>
 <div>
    <ul class="list">
      <li v-for="(item,i) in article" :key='i' class="item">
        <nuxt-link :to="{ name:'article-id',params:{id:article[i].id}}">
          <h2 class="item-title">{{ article[i].title.rendered }}</h2>
          <p class="item-excerpt" v-html="article[i].excerpt.rendered"></p>
        </nuxt-link>
        <p>
          <span class="item-time">{{ article[i].date }}</span>
        </p>
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
