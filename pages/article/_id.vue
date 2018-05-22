<template>
  <div>
    <!-- id:{{ $route.params.id }}
    date:{{ $route.params.date }} -->
    <div class="Article-body">
      <div class="article-header">
        <h2 class="article-title">{{ ArticleTitle }}</h2>
        <p class="article-time">{{ ArticleTime }}</p>
        <div class="article-excerpt" v-html=" ArticleExcerpt "></div>
      </div>
      <div v-html="ArticleContent"></div>
    </div>
  </div>
</template>

<script>
    import axios from 'axios'
    export default {
        head(){
            return {
                title: '文章'
            }
        },
        data(){
          return {
              Articleid: this.$route.params.id,
              ArticleTitle: '',
              ArticleExcerpt: '',
              ArticleContent: '',
              ArticleTime:''
          }
        },
        created(){
            this.getArticle();
        },
        methods:{
          getArticle(){
            axios.get("http://www.likecn.cn/wp-json/wp/v2/posts/" + this.Articleid)
            .then(res => {
                console.log(res.data);
                let isUseTime,
                    oldTime = res.data.date;
                this.ArticleTitle = res.data.title.rendered
                this.ArticleExcerpt = res.data.excerpt.rendered
                this.ArticleContent = res.data.content.rendered
                isUseTime = oldTime.substring(0,10)
                this.ArticleTime = isUseTime;
            })
          }
        }
    }
</script>

<style scoped>

</style>
