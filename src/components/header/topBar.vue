<template>
    <el-row class="m-header-topbar m-header">
        <el-col :span="10">
            <geo/>
        </el-col>
        <el-col :span="14">
            <mnav/>
        </el-col>
    </el-row>
</template>

<script>
import geo from './geo'
import Mnav from './nav'
export default {
  components: {
    geo,
    Mnav
  }
}
</script>

<style lang="sass" >
    @import  '@/assets/css/public/header/topbar.scss'
</style>
