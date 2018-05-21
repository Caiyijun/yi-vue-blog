<template>
    <div>
        <!-- id:{{ $route.params.id }} -->
        <p>目前所在分类: {{ categoriesname }} </p>
        <ul>
            <li v-for="(item,i) in thisCategoriesArticle" :key="i" >
              <nuxt-link :to="{ name:'article-id',params:{ id:thisCategoriesArticle[i].id }}">
                <h2>{{ thisCategoriesArticle[i].title.rendered }}</h2>
                <p v-html="thisCategoriesArticle[i].excerpt.rendered"></p>
              </nuxt-link>
                <p>
                    <span>{{ thisCategoriesArticle[i].date }} </span>
                </p>
            </li>
        </ul>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        head(){
            return {
                title: '文章分类'
            }
        },
        data(){
            return {
                catrgoriesid: this.$route.params.id,
                categoriesname:'',
                thisCategoriesArticle:[]
            }
        },
        created(){
            this.getinfo();
        },
        methods:{
            getinfo(){
                axios.all([
                    axios.get('http://www.likecn.cn/wp-json/wp/v2/posts'),
                    axios.get('http://www.likecn.cn/wp-json/wp/v2/categories/' + this.catrgoriesid),
                    // axios.get('http://www.likecn.cn/wp-json/wp/v2/comments')
                ])
                .then(axios.spread((article,categories)=>{
                    console.log(article.data)
                    // console.log(categories.data)
                    this.categoriesname = categories.data.name;
                    let thatArticle = []
                    for (let i = 0; i < article.data.length; i++){
                        if( article.data[i].categories[0] == this.catrgoriesid ){
                            thatArticle.push(article.data[i])
                        }
                    }
                    this.thisCategoriesArticle = thatArticle;
                    console.log(thatArticle);
                    // this.article = articleres.data
                    // var articleData = articleres.data,
                    //     articleDate = [],
                    //     dateList = [];
                    // console.log(articleData);
                    // for (let i = 0; i < articleData.length; i++){
                    //     let Arr = articleres.data[i].date;
                    //     articleDate.push(Arr);
                    // }
                    // for(let i=0; i<articleDate.length; i++){
                    // let arrlist = articleDate[i]
                    // let arrStred = arrlist.substring(0,10)
                    // dateList.push(arrStred)
                    // }
                    // console.log(dateList);
                    // this.AllDateList = dateList;
                }))
                .catch((error)=>{})
            }
        }
    }
</script>

<style scoped>

</style>
