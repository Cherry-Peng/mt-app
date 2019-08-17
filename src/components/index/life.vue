<template>
  <div class="m-life">
    <el-row>
      <ul class="nav">
        <li>
          <router-link to="/" class="takeout">美团外卖</router-link>
        </li>
        <li>
          <router-link to="/" class>猫眼电影</router-link>
        </li>
        <li>
          <router-link to="/" class>美团酒店</router-link>
        </li>
        <li>
          <router-link to="/" class="apartment">民宿/公寓</router-link>
        </li>
        <li>
          <router-link to="/" class="business">商家入驻</router-link>
        </li>
        <li>
          <router-link to="/" class>美团公益</router-link>
        </li>
      </ul>
    </el-row>
    <el-row>
      <el-col :span="14">
        <slider />
      </el-col>
      <el-col :span="4">
        <img
          src="http://p0.meituan.net/codeman/e473bb428f070321269b23370ff02ba956209.jpg"
          class="m-life-pic"
        />
      </el-col>
      <el-col :span="6">
        <div class="m-life-login">
          <img src="//s0.meituan.net/bs/fe-web-meituan/e350c4a/img/avatar.jpg" alt />
          <p class="m-life-login-name">Hi,{{$store.state.userName ? $store.state.userName : '你好'}}!</p>
          <p v-if="!$store.state.userName">
            <router-link :to="{naem:'register'}">
              <el-button round>注册</el-button>
            </router-link>
          </p>
          <p v-if="!$store.state.userName"> 
            <router-link :to="{name:'login'}">
              <el-button round>立即登陆</el-button>
            </router-link>
          </p>
        </div>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="7">
        <div class="m-life-hotel"></div>
      </el-col>
      <el-col :span="7">
        <div class="m-life-music"></div>
      </el-col>
      <el-col :span="4">
        <div class="m-life-coop"></div>
      </el-col>
      <el-col :span="6" class="m-life-downapp">
        <img src="//s1.meituan.net/bs/fe-web-meituan/60ac9a0/img/download-qr.png" alt="下载APP" />
        <p>美团APP手机版</p>
        <p class="last-p">
          <span>1元起</span>
          吃喝玩乐
        </p>
      </el-col>
    </el-row>
  </div>
</template>
<script>
import Slider from "./slider";
export default {
  components: {
    Slider
  }
};
</script>

<style lang="sass" >
    @import "@/assets/css/index/life.scss"
</style>

