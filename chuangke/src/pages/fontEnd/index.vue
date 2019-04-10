<template>
 <div>

  <news></news>
 <image class="titleImg" src="../../static/images/bg5.jpg" alt=""/>
   
  <div class="titleBox">
    <image src="../../static/images/tu2.png" alt=""/>
    <span>后端开发</span>
    <div class="line"></div>
  </div>
  <div class="contentDetail">
    <span>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      根据正在处理的应用程序的大小和范围，后端开发人员要做的事情用很大的不同。在我是一个后端开发人员时，我做了很多工作，工作与应用程序中的业务逻辑，以及以前端提取和检索数据。在Web开发
      世界中，大多是后端开发人员从事与构建他们正在工作的应用程序背后的实际逻辑。通常，前端开发人员构建用户界面，而后端开发人员编写代码，处理业务逻辑。总的来说
      后端就是为了让服务器、应用、数据库能够彼此交互。
      
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
  color: black
}



</style>
