<template>
    <div class="slide">
          <el-carousel >
      <el-carousel-item v-for="(item,index) in imgList" :key="index">
            <img :src="item.img">
      </el-carousel-item>
    </el-carousel>
    </div>
</template>

<script>
export default {
    data(){
        return {
            imgList:[
                {
                    url:"#xxx",
                    img:"http://p0.meituan.net/codeman/a97baf515235f4c5a2b1323a741e577185048.jpg"
                }, {
                    url:"#xxx",
                    img:"http://p0.meituan.net/codeman/a97baf515235f4c5a2b1323a741e577185048.jpg"
                }, {
                    url:"#xxx",
                    img:"http://p0.meituan.net/codeman/a97baf515235f4c5a2b1323a741e577185048.jpg"
                }, {
                    url:"#xxx",
                    img:"http://p0.meituan.net/codeman/a97baf515235f4c5a2b1323a741e577185048.jpg"
                }
            ]
        }
    }
}
</script>
