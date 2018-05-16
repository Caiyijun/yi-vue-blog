<template>
  <div>
    <el-container>
      <elnav></elnav>
      <elcontain>
        <nuxt/>
      </elcontain>
      <el-footer>12</el-footer>
    </el-container>
  </div>
</template>

<script>
import elnav from '~/components/el-nav.vue'
import elcontain from '~/components/el-contain.vue'
export default {
  components:{
    elnav
  }
}
</script>


<style>
</style>
