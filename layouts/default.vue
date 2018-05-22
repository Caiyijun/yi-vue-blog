<template>
    <el-container>
      <elnav :span='10' :offset='2'></elnav>
      <el-main>
        <div class="wrap">
          <el-row :gutter="20">
            <elside></elside>
            <el-col :span="14" class="contain"> 
                <nuxt/>
            </el-col>
          </el-row>
        </div>
      </el-main>
      <el-footer>
        <elfoot></elfoot>
      </el-footer>
    </el-container>
</template>

<script>
import elnav from '~/components/el-nav.vue'
import elcontain from '~/components/el-contain.vue'
import elside from '~/components/el-side.vue'
import elfoot from '~/components/el-foot.vue'
export default {
  components:{
    elnav,
    elcontain,
    elside,
    elfoot
  }
}
</script>


<style>
.contain{
    float: left;
    /* position: relative; */
}
</style>
