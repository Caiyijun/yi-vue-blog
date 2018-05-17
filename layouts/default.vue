<template>
  <div class="wrap">
    <el-container>
      <elnav></elnav>
      <el-main>
        <el-row :gutter="20">
          <elside></elside>
          <el-col :span="20"> 
            <nuxt/>
          </el-col>
        </el-row>
      </el-main>
      <el-footer>
        <elfoot></elfoot>
      </el-footer>
    </el-container>
  </div>
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
</style>
