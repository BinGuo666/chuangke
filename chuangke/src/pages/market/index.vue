<template>
 <div>
  <news></news>
 <image class="titleImg" src="../../static/images/bg3.jpg" alt=""/>
   
  <div class="titleBox">
    <image src="../../static/images/tu3.png" alt=""/>
    <span>市场调研</span>
    <div class="line"></div>
  </div>
  <div class="contentDetail">
    <span>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      市场调研是一种把消费者及公共部门和市场联系起来的特定活动一一这些信息用以识别和界定市场营销机会和问题，产生、改进和评价营销活动，监控营销绩效，增进对营销过程的理解。市场调研实际上是一项寻求市场与企业之间“共谐”的过程。市场调研犹如婚前健康检查，如果忽略它，就可能产生低能儿，到那时再一掷千金搞销售，好似给低能儿增加营养，又能起多大作用？因为市场营销的观念意味着消费者的需求应该予以满足，所以公司内部人士一定要聆听消费者的呼声，通过市场调研，“倾听”消费者的声音。当然，营销调研信息也包括除消费者之外的其他实体的信息。主要以需求出发，寻找和协助项目的开展！
      主要以后端学习和项目调研为主，后期可转型为后端、前端或全栈工程师！
      </span>
  </div>
  
     <footers></footers>
 </div>
</template>

<script>
import footers from "@/components/footer";
import news from "@/components/new";
 export default {
   data () {
     return {

     }
   },
   components: {
     footers,
     news
   }
 }
</script>

<style>
.titleImg{
  width: 90%;
  height: 300rpx;
  position: relative;
  margin-left: 5%;
}

/* title样式 */
.titleBox{
  width: 100%;
  height: 60rpx;
  position: relative;
  /* background-color: rgba(80, 47, 47, 0.452); */
  margin-top: 20rpx;
}

.titleBox image{
  width: 40rpx;
  height: 40rpx;
  position: relative;
  float: left;
  margin-left: 10rpx;
  margin-top: 10rpx;
}
.titleBox span{
  position: relative;
  float: left;
  color: rgba(13, 134, 190, 0.767);
  letter-spacing: 4rpx;
  line-height: 60rpx;
  margin-left: 15rpx;
  font-weight: 600;
  font-size: 30rpx;
}
.titleBox .line{
  width: 70%;
  height: 0;
  border-top: 1px solid rgba(13, 134, 190, 0.767);
  float: left;
  margin-top: 29rpx;
  margin-left: 5rpx;
}

/* 中部内容部分 */
.contentDetail{
  width: 90%;
  margin-left: 5%;
  margin-top: 10rpx;
}
.contentDetail span{
  font-size: 30rpx;
  letter-spacing: 2rpx;
  color: black;
}


</style>
