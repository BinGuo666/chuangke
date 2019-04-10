<template>
 <div>
<!-- 头部提示 -->
   <div id="news">
     <image src="../../static/images/tip0.png" alt=""/>
     <span>报名截止时间为4月13号0点！敬请留意！</span>
   </div>

 </div>
</template>

<script>
 export default {
   data () {
     return {

     }
   },
   components: {

   }
 }
</script>

<style>
/* 头部提示信息 */
#news{
  width: 100%;
  height: 50rpx;
  position: relative;
  background-color: rgba(226, 175, 34, 0.356);
}
#news image{
  width: 24rpx;
  height: 24rpx;
  position: relative;
  float: left;
  margin-left: 15rpx;
  margin-top: 14rpx;
}
#news span{
  font-size: 24rpx;
  line-height: 50rpx;
  margin-left: 15rpx;
  letter-spacing: 3rpx;
  float: left;
  color: rgba(219, 76, 20, 0.753);
}
 
</style>
