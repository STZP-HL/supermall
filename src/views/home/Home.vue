<template>
  <!-- <h2>首页</h2> -->
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
  <home-swiper :banners="banners"/>
  <recommend-view :recommend="recommends"/>
  <feature-view/>
  <tab-control :titles="['流行','新款','精选']"/>

  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar';
 import TabControl from 'components/content/tabControl/TabControl'


import HomeSwiper from './childComps/HomeSwiper.vue'
import RecommendView from './childComps/RecommendView.vue'
import FeatureView from './childComps/FeatureView.vue'


import {getHomeMultidata} from 'network/home';


  export default {
    name: "Home",
    components:{
      NavBar,
      TabControl,
      HomeSwiper,
      RecommendView,
      FeatureView
    },
   
    data() {
      return {
        //result:null
        banners:[],
        recommends:[]
      }
    },
    created(){
      //1.发送网络请求，请求多个数据
      getHomeMultidata().then(res=>{
        //this.result=res;//将res赋值给result进行保存。避免函数调用结束后被回收掉。
        this.banners=res.data.banner.list;
        this.recommends=res.data.recommend.list;
      })

    }
  }

</script>

<style scoped>
#home{
  padding-top: 44px;
}
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }
</style>
