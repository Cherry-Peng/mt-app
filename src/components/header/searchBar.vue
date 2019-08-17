<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col :span="3" class="left">
        <img src="https://s0.meituan.net/bs/fe-web-meituan/fa5f0f0/img/logo.png" alt="美团" />
      </el-col>
      <el-col :span="15" class="center">
        <div class="wrapper">
          <el-input
            v-model="searchWord"
            placeholder="请输入内容"
            @focus="focus"
            @blur="blur"
            @input="input"
          ></el-input>
          <el-button type="primary" icon="el-icon-search"></el-button>
          <dl class="hotPlace" v-if="isHotPlace">
            <dt>热门搜索</dt>
            <dd v-for="(item,index) in hotPlaceList" :key="index">
              <router-link :to="{name:'goods',params:{name:item}}">{{item}}</router-link>
            </dd>
          </dl>
          <dl class="searchList" v-if="isSearchList">
            <router-link
              tag="dd"
              :to="{name: 'goods', params: {name: item}}"
              v-for="item in searchList"
              :key="item"
            >
              <!-- <router-link to="/s">{{item}}</router-link> -->
              <router-link :to="{name: 'goods', params: {name: item}}">{{item}}</router-link>
            </router-link>
          </dl>
        </div>
        <p class="suggest">
          <!-- <a :href="item" v-for="(item,index) in suggestList" :key="item">{{item}}</a> -->
          <router-link
            v-for="(item, index) in suggestList"
            :key="item + '~' + index"
            :to="{name: 'goods', params: {name: item}}"
          >{{item}}</router-link>
        </p>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {};
</script>
<style lang="sass" >
    @import  '@/assets/css/public/header/index.scss'
    @import '@/assets/css/public/header/search.scss'
</style>
<script>
import api from "@/api/index.js";
export default {
  data() {
    return {
      searchWord: "",
      isFocus: false,
      hotPlaceList: ["太平洋影城", "太平洋影城", "太平洋影城"],
      searchList: ["火锅", "火锅1", "火锅2", "火锅3"],
      suggestList: [
        "太平洋影城",
        "海豚湾梦幻水上乐园",
        "南部新城置信·逸都城",
        "在水一方水上乐园",
        "小鱼洞大桥遗址"
      ]
    };
  },
  created() {
    api.getSearchHotWord().then(res => {
      this.hotPlaceList = res.data.data;
      this.suggestList = res.data.data;
    });
  },
  computed: {
    isHotPlace() {
      return this.isFocus && !this.searchWord;
    },
    isSearchList() {
      return this.isFocus && this.searchWord;
    }
  },
  methods: {
    input() {
      let val =this.searchWord
      api.searchWords().then(res => {
        this.searchList = res.data.data.list.filter((item,index)=>{
          return item.indexOf(val) > -1
        })
      });
    },
    focus() {
      this.isFocus = true;
    },
    blur() {
      let that = this;
      setTimeout(function() {
        that.isFocus = false;
      }, 200);
    }
  }
};
</script>
