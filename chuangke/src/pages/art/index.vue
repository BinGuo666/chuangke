<template>
 <div>
  <news></news>
 <image class="titleImg" src="../../static/images/bg2.png" alt=""/>
   
  <div class="titleBox">
    <image src="../../static/images/tu4.png" alt=""/>
    <span>美工设计</span>
    <div class="line"></div>
  </div>
  <div class="contentDetail">
    <span>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      美工设计，是根据用户希望向浏览者传递的信息（包括产品、服务、理念、文化），进行网站功能策划，然后进行的页面设计美化工作。
网页设计的工作目标，是通过使用更合理的颜色、字体、图片、样式进行页面设计美化，在功能限定的情况下，尽可能给予用户完美的视觉体验。高级的网页设计甚至会考虑到通过声光、交互等来实现更好的视听感受。与其同时
，美工设计也算是半个前端，在学习切图的同时，也可以学习网页、app页面的构建，后期也可以逐步转型为前端。
      
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
