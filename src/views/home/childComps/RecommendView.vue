<template>
  <div class="recommend">
      <div class="recommend-item" v-for="(item,index) in recommend" :key="index">
          <a :href="item.link">
              <img :src="item.image" alt="">
              <div>{{item.title}}</div>
          </a>
      </div>
  </div>
</template>

<script>
export default {
    name:'RecommendView',
    props:{
        recommend:Array,
        default:{
            return:[]
        }
    }
}
</script>

<style >
  .recommend{
     display: flex;
     padding: 20px 0 10px;
     border-bottom: 20px solid #ccc;
 }

.recommend-item{
    flex:1;
    text-align: center;
    font-size:12px;
}
/* 60-80px */
.recommend-item img{
    width:80px;
    margin-bottom: 12px;
}
</style>
