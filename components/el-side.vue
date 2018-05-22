<template>
    <el-col :span="4" :offset="2" class="nav-col">
        <div class="sidenav">
            <ul class="nav-side">
                <li class="sidemenu" v-for="(item,i) in categories" :key="i">
                    <nuxt-link :to="{name:'categorie-id',params:{id:categories[i].id}}">
                        <i></i>
                        <span>{{ categories[i].name }}</span>
                    </nuxt-link>
                </li>
            </ul>
        </div>
    </el-col>
</template>

<script>
import axios from 'axios'
export default {
    data(){
        return {
            categories:''
        }
    },
    created: function(){
        axios.get('http://www.likecn.cn/wp-json/wp/v2/categories')
        .then(res => {
            // console.log(res);
            this.categories = res.data;
        })
        .catch(error => {
            alert('网络错误，不能访问');
        });
    }
}
</script>

<style>
.sidenav{
    position: fixed;
    top: 110px;
    width: 160px;
    z-index:999;
}
.nav-side{
    background: rgba(255,255,255,0.2);
    font-size: 14px;
    color: #444;
    border-radius: 8px;
    box-shadow: 0 0 30px rgba(0,0,0,0.03);
    transition: all .5s ease;
}
.nav-side:hover{
    box-shadow: 0 0 30px rgba(0,0,0,0.08);
}
.nav-side .sidemenu{
    height:40px;
    line-height: 40px;
    padding: 0 25px;
    transition: all .5s ease;
}
.nav-side .sidemenu:hover{
    background: #409eff;
    color: #fff;
}
.nav-side .sidemenu a{
    display: block;
    color: inherit
}
.nav-col:before{
    content: "";
    display: block;
    height: 1px;
    position: relative;
}
</style>
