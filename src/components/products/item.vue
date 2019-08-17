<template>
  <dl class="s-item">
    <dt>
      <img :src="meta.image" alt />
    </dt>
    <dd>
      <router-link tag="h3" :to="{name:'productDetail'}">{{meta.title}}</router-link>
      <p>
        <el-rate
          v-model="meta.score"
          disabled
          show-score
          text-color="#ff9900"
          score-template="{value}"
        ></el-rate>
        <span v-if="meta.score > 4.5">很好</span>
        <span v-else-if="meta.score > 4">好</span>
        <span v-else-if="meta.score > 3.5">不错</span>
        <span v-else-if="meta.score > 3">一般</span>
        <span v-else>很差</span>
        <span class>{{meta.score}}</span>
        <span class="s-item-comment-tota">{{meta.commentNum}}人评论</span>
      </p>
      <p>
        <span class="s-item-type">
          <span v-for="(v,i) in meta.tab" :key="v">{{ v + (i < meta.tab.length - 1 ? '|' : '')}}</span>
        </span>
        <span class="s-item-addr">{{meta.address}}</span>
        <span>
          <a href="#">
            <i class="el-icon-location"></i>
          </a>
        </span>   
      </p>
      <p>
        <span class="s-item-price">人均${{meta.avgPrice}}</span>
      </p>
      <ul class="deal-items">
        <li class="items" v-for="(item,index) in meta.dealItems.slice(0,2)" :key="index">
          <p class="deal-title">{{item.title}}</p>
          <p>
            <span class="deal-price">${{item.price}}</span>
            <span class="deal-old-price">门市价${{item.counterPrice}}</span>
            <span class="deal-sales">已售{{item.saleNum}}</span>
          </p>
        </li>
      </ul>
    </dd>
  </dl>
</template>
<script>
export default {
  props: ["meta"]
};
</script>