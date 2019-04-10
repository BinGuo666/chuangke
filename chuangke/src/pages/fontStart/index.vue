<template>
 <div>
  <news></news>

 <image class="titleImg" src="../../static/images/bg6.jpg" alt=""/>
   
  <div class="titleBox">
    <image src="../../static/images/tu1.png" alt=""/>
    <span>前端开发</span>
    <div class="line"></div>
  </div>
  <div class="contentDetail">
    <span>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      前端开发是创建Web页面或app等前端界面呈现给用户的过程，通过HTML，CSS及JavaScript以及衍生出来的各种技术、框架、解决方案，来实现互联网产品的用户界面交互。它从网页制作演变而来，名称上有很明显的时代特征。在互联网的演化进程中，网页制作是Web1.0时代的产物，早期网站主要内容都是静态，以图片和文字为主，用户使用网站的行为也以浏览为主。随着互联网技术的发展和HTML5、CSS3的应用，现代网页更加美观，交互效果显著，功能更加强大。
      </span>
  </div>
  
     <footers></footers>
 </div>
</template>

<script>
import footers from "@/components/footer";
import news from "@/components/new"
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
