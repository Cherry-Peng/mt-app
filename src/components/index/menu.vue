<template>
    <div class="m-menu">
       <dl class="nav" @mouseleave="menuLeave">
           <dt>全部分类</dt>
           <dd v-for="(item,index) in menuList" :key="index" @mouseenter="menuEnter(item)">
              <i :class="item.icon"></i>
              {{item.name}}
              <span class="arrow"></span>
           </dd>
       </dl>
       <div v-if="curDetail" class="detail" @mouseenter="detailEnter" @mouseleave="detailLeave">
           <template v-for="(item,index) in curDetail.items">
               <h2 :key="index">{{item.title}}</h2>
               <span v-for="(v,i) in item.items" :key="i+'_'+v">{{v}}</span>
           </template>
       </div>
    </div>
</template>
<script >
import api from '@/api/index.js'
export default {
    data(){
        return {
            curDetail:null,
            menuList:[{
                name:"美食",
                icon:"food",
                items:[
                    {
                        title:"美食",
                         items:['代金券','甜点饮品','火锅','自助餐','小吃','快餐','日韩料理','西餐','聚餐宴请','烧烤烤肉','东北菜','川湘菜',
                        '江浙','菜香锅烤鱼','粤港菜','中式烧烤/烤串','西北菜','咖啡酒吧','茶馆','云贵菜','东南亚菜','海鲜素食','台湾/客家菜',
                        '创意菜,汤/粥/炖菜','蒙餐','新疆菜','其他美食','京菜','鲁菜'
                        ]
                    }]
                },
                {
                name:"外卖",
                icon:"takeout",
                items:[
                    {
                        title:"外卖",
                         items:["美团外卖"]
                    }]
                },
                 {
                name:"酒店",
                icon:"hotel",
                items:[
                    {
                        title:"酒店星级",
                         items:["进典型",'舒适/三心','高档/四星','豪华/五星']
                    }]
                },
            ]
        }
    },
    created(){
        api.getMenuList().then(res=>{
            this.menuList = res.data.data
        })
    },
    methods:{
        menuEnter(item){
            this.curDetail = item
        },
        menuLeave(){
            let that =this
            this.timer = setTimeout(function(){
                that.curDetail = null;
            },200)
        },
       detailEnter(){
            clearTimeout(this.timer)
        },
        detailLeave(){
        this.curDetail = null;
        }
    }
}
</script>