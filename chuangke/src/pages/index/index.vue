<template>
 <div>
   <!-- 头部提示 -->
   <news></news>


   <!-- 轮播图 -->
   <swiper style="z-index:2;" class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
        <block v-for="(item, index) in images" :key="index">
            <swiper-item  style="width:100%;height:100%;">
                <image style="width:100%;height:125%;" :src="item.url" class="slide-image" mode="aspectFill"/>
            </swiper-item>
        </block>
    </swiper> 
  
  <!-- 中间内容 -->
  <!-- 招新方向 -->
  <div class="titleBox">
    <image src="../../static/images/tip5.png" alt=""/>
    <span>招新方向</span>
    <div class="line"></div>
  </div>

  <div class="direction connect">
    <ul>
      <li class="fontStart" @click="fontStartPage">
        <image src="../../static/images/tu1.png" alt=""/>
        <span>前端</span>
        <div></div>
      </li>
      <li @click="fontEndPage">
        <image src="../../static/images/tu2.png" alt=""/>
        <span>后端</span>
        <div></div>
      </li>
      <li @click="marketPage">
        <image src="../../static/images/tu3.png" alt=""/>
        <span>市场</span>
        <div></div>
      </li>
      <li @click="artPage">
        <image src="../../static/images/tu4.png" alt=""/>
        <span>美工</span>
        <div></div>
      </li>
    </ul>
  </div>


  <!-- 指导老师 -->
  <div class="titleBox">
    <image src="../../static/images/tip6.png" alt=""/>
    <span>指导老师</span>
    <div class="line"></div>
  </div>
  <div class="teacher connect">

      <image class="personImg" src="../../static/images/person.jpg" alt=""/>
    
    <div class="personBox">
      <div class="title">
        李绍强
        <span>副教授</span>
      </div>
      <div class="detail">
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;李绍强，男，副教授，物联网工程教研室主任。信息技术与工程学院硬件教研室教师。毕业于华南理工大学软件学院。
      </div>
    </div>
    
  </div>
  <div class="teacher connect">

      <image class="personImg" src="../../static/images/person1.png" alt=""/>
    
    <div class="personBox">
      <div class="title">
        何文海
        <span>副教授</span>
      </div>
      <div class="detail">
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;何文海，男，副教授，软件教研室主任。毕业于中山大学,参编《大学计算机网络基础》等4部教材。
      </div>
    </div>
    
  </div>
  <div class="teacher connect">

      <image class="personImg" src="../../static/images/person2.png" alt=""/>
    
    <div class="personBox">
      <div class="title">
        陈卫丽
        <span>讲师</span>
      </div>
      <div class="detail">
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;陈卫丽，女，毕业于华南理工大学，获得硕士学位。主持校企合作项目《升级改造晶振行业日老化测试软件》
      </div>
    </div>
    
  </div>
  <!-- 创客介绍 -->
  <div class="titleBox">
    <image src="../../static/images/tip7.png" alt=""/>
    <span>创客介绍</span>
    <div class="line"></div>
  </div>

  <div class="introduce connect">
    <div class="introdue_title">创客空间</div>
     <image class="personImg" src="../../static/images/chuangke.jpg" alt=""/>
     <div class="detail"> 
       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{{chuangkeText}}
     </div>
  </div>
  <!-- 版权所有 -->
  
 
   <!-- 选择动画 -->
  <div id="choose" v-if="!addmy" >
    <div class="circle"></div>
    <ul >
      <li :class="change1" class="foreEnd"  @click="selects(0)">
        <span>前端开发</span><div class="ripple1 ri11" ></div> <div class="ripple2 ri21"></div>
        <image v-if="select[0].dec" src="../../static/images/true1.png" alt=""/>
        </li>
      <li :class="change2" class="backEnd" @click="selects(1)">
        <span>后端开发</span><div class="ripple1 ri12" ></div> <div class="ripple2 ri22"></div>
        <image v-if="select[1].dec" src="../../static/images/true1.png" alt=""/>
        </li>
      <li :class="change3" class="market" @click="selects(2)">
        <span>市场调研</span><div class="ripple1 ri13" ></div> <div class="ripple2 ri23"></div>
        <image v-if="select[2].dec" src="../../static/images/true1.png" alt=""/>
        </li>
      <li :class="change4" class="consider" @click="selects(3)">
        <span>美工设计</span><div class="ripple1 ri14" ></div> <div class="ripple2 ri24"></div>
        <image v-if="select[3].dec" src="../../static/images/true1.png" alt=""/>
        </li>
    </ul>
    <div class="decition" :class="decitionClass" @click="getForm"><span>{{chooseDate}} </span></div>
    <div class="tip">最多只能选择两个方向</div>
  </div>

 <!-- 掩盖层 -->
 <div class="cover"  @click="reBack" v-if="!addmy">
 </div> 
<!-- 加入按钮 -->
  <button id="add" @click = "clickOne" :class="timeoutClass" :disabled='timeout' v-if="addmy">  
    申请加入
  </button>
 <footers></footers>
 </div>
 
</template>

<script>
import footers from "@/components/footer";
import news from "@/components/new";
 export default {
 
   data () {
     return {
       indicatorDots: true,
       timeout:false,
       timeoutClass:'add1',
      autoplay: true,
      interval: 3000,
      duration: 500,
      selects1:false,
      startX:0,
      startY:0,
      moveX:0,
      moveY:0,
      selectCom:0,
      select:[{dec:false,name:"前端开发"},{dec:false,name:"后端开发"},{dec:false,name:"市场调研"},{dec:false,name:"艺术设计"}],
      chooseDate:"Which is your Decition ? ",
      selectIt:[],
      addmy: true,
      decition:false,
      change1:'choose1',
      change2:'choose1',
      change3:'choose1',
      change4:'choose1',
      change5:'choose1',
      chuangkeText:"创客空间是一个同学们能分享兴趣--多数是电脑，技术，科学，数组和电子艺术（也包括其他的各方面）--合作，动手，创造的地方。创客空间被看作是一个计算机科学研究团队！。在这里，你可以学到更多课堂上学不到的专业知识，遇到你意想不到的机遇和挑战！创客中的同学们基本揽括了系内外各类计算机比赛三分之二的奖项！不仅如此，创客还与校外企业建立了合作关系。在这里，不仅能学习到更专业的知识、确定就业方向，还能够提前参与企业项目，获得更多的知识和项目经验！从创客出去的师兄师姐无不是社会中的佼佼者！在创客，不仅提供了一个安静舒适的环境、优秀的导师指导、更多的项目实践，还提供空调、wifi、有线宽带等各种设置。你还在等什么呢？赶紧加入我们吧！------报名时间为：4月5号到4月12号！面试时间为：4月14号晚上7点30分！面试地点：创客空间103.（请自行填写打印申请表）",
      decitionClass:'decition1',
      images:
        [
        {url:"../../static/images/bg1.jpg"},
        {url:"../../static/images/bg8.jpg"},
        {url:"../../static/images/bg2.png"},
        {url:"../../static/images/bg3.jpg"},
        {url:"../../static/images/bg5.jpg"},
        {url:"../../static/images/bg6.jpg"}
       
        ]
      
     }
     computed:{
     }

     
   },
   components: {
     footers,
     news
   },
   methods:{
     clickOne(e){
       this.addmy = false;
       this.decition = false;
       this.change1 = this.decition? 'choose1':'choose2'
       this.change2 = this.decition? 'choose1':'choose3'
       this.change3 = this.decition? 'choose1':'choose4'
       this.change4 = this.decition? 'choose1':'choose5'
       this.change5 = this.decition? 'choose1':'choose6'
       this.change6 = this.decition? 'choose1':'choose7'
       //清空申请选项
       this.select.forEach((item) => {
         item.dec = false;
         this.selectCom = 0;
       });
       this.chooseDate = "Which is your Decition ? ",
         this.decitionClass = 'decition1';
     },
     reBack(e){
       this.addmy = true;
       this.decition = true;
       this.change1 = this.decition? 'choose1':'choose2'
       this.change2 = this.decition? 'choose1':'choose3'
       this.change3 = this.decition? 'choose1':'choose4'
       this.change4 = this.decition? 'choose1':'choose5'
       this.change5 = this.decition? 'choose1':'choose6'
       this.change6 = this.decition? 'choose1':'choose7'
     },
     moveBtn(e){
       console.log(e);
     },
     selects(i){
      //  this.select.forEach((item) => {
      //    if(item.dec === true){
      //      console.log(item);
      //    }
      //  });
       if(this.select[i].dec==true){
           this.select[i].dec = false;
           this.selectCom--;    
       }else{
         if(this.selectCom<2){
           this.select[i].dec = true;
           this.selectCom++;
         }
       }
       if(this.selectCom>0){
         this.chooseDate = "确认方向",
         this.decitionClass = 'decition2';
       }else{
         this.chooseDate = "Which is your Decition ? ",
         this.decitionClass = 'decition1';
       }
     },
     fontStartPage(){
       wx.navigateTo({
            url:'/pages/fontStart/main'
        })
     },
     fontEndPage(){
       wx.navigateTo({
            url:'/pages/fontEnd/main'
        })
     },
     marketPage(){
       wx.navigateTo({
            url:'/pages/market/main'
        })
     },
     artPage(){
       wx.navigateTo({
            url:'/pages/art/main'
        })
     },
     getForm(){
       if(this.selectCom>0){
         let i = 0;
         this.select.forEach((item)=>{
           if(item.dec == true){
             this.selectIt[i++]=item.name;
           }
         })
         wx.navigateTo({
            url:'/pages/form/main?select1='+this.selectIt[0]+'&select2='+this.selectIt[1]
        })
       }
     }

   },
   onUnload(){
    console.log("onunload")
  },
  onShow(){
    this.addmy=true,
      this.decition=false,
      this.select.forEach((item)=>{
          item.dec = false;
      })
      this.selectIt = [];
      let date1 = new Date("2019-04-01 00:00:00");
      let date2 = new Date();
      let time1 = (date2-date1)/3600/1000/24;
      if(time1>=12){
        this.timeoutClass = 'add2',
        this.timeout = true;
      }
      console.log(date1);
  },
  onShareAppMessage(){
    console.log("分享成功！");
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


/* title样式 */
.titleBox{
  width: 100%;
  height: 60rpx;
  position: relative;
  /* background-color: rgba(80, 47, 47, 0.452); */
  margin-top: 30rpx;
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


/* 内容样式 */
.connect{
  width: 100%;
  position: relative;

}
.direction{
  height: 130rpx;
}
.direction ul li{
  width: 185rpx;
  height: 130rpx;
  list-style: none;
  float: left;
  position: relative;
  margin-right: 2rpx
}
.direction ul li:nth-child(1){
    margin-left: 2rpx
}
.direction ul li div{
  width: 100%;
  height: 100rpx;
  position: absolute;
  top: 15rpx;

}
.direction ul li:nth-child(1) div{
   border-right: 2px solid rgba(153, 153, 153, 0.411);
}
.direction ul li:nth-child(2) div{
   border-right: 2px solid rgba(153, 153, 153, 0.411);
}
.direction ul li:nth-child(3) div{
   border-right: 2px solid rgba(153, 153, 153, 0.411);
}
.direction ul li image{
  width: 60rpx;
  height: 60rpx;
  position: absolute;
  display: block;
  left: 50%;
  transform: translateX(-50%);
  top: 15rpx;
}
.direction ul li span{
  font-size: 32rpx;
  width: 100%;
  display: block;
  text-align: center;
  position: absolute;
  letter-spacing: 4rpx;
  bottom: 2rpx;
}
/* 指导老师模板 */
.teacher{
  height: 200rpx;
  background-color: rgba(124, 158, 132, 0.123);
  margin: 20rpx 0 30rpx 0;
}
.teacher .personImg{
  position: relative;
  width: 120rpx;
  height: 160rpx;
  left: 20rpx;;
  top: 20rpx;
  float: left;
}
.teacher .personBox{
  position: absolute;
  right: 20rpx;
  width: 570rpx;
  margin-left: 10rpx;
  height: 100%;
  
  /* background-color: rgba(180, 122, 122, 0.37); */
}
.teacher .personBox .title{
  width: 100%;
  position: relative;
  font-size: 35rpx;
  height: 50rpx;
  font-weight: 600;
  letter-spacing: 2rpx;
  margin-left: 20rpx;
  line-height: 50rpx;
  margin-top: 10rpx;
}
.teacher .personBox .title span{
  font-size: 32rpx;
  font-weight: 500;
  line-height: 50rpx;
}
.teacher .personBox .detail{
  width: 100%;

  position: relative;
  font-size: 28rpx;
  margin-top: 10rpx;
  background-color: rgba(255, 255, 255, 0.616);
  letter-spacing: 2rpx;
  border-radius: 10rpx;
}


/* 创客介绍模块 */
.introdue_title{
  position: relative;
  width: 100%;
  height: 50rpx;
  line-height: 50rpx;
  text-align: center;
  font-size: 38rpx;
  letter-spacing: 4rpx;
  left: -6rpx;
  font-weight: 800;
  margin-bottom: 20rpx;
}

.introduce{
  background-color: rgba(65, 140, 175, 0.068);
  padding: 20rpx;
  margin-top: 20rpx;
}
.introduce image{
  position: relative;
  width: 400rpx;
  height: 300rpx;

  float: left;
  margin-right: 20rpx;
  /* margin-bottom: 10rpx; */
}
.introduce .detail{
  margin-right: 30rpx;
  font-size: 32rpx;
  letter-spacing: 2rpx;
  
}

/* 申请加入样式 */
#add{
  width: 150rpx;
  height: 150rpx;
  position:relative; 
  padding-top: 30rpx;
  font-size: 35rpx;
  line-height: 45rpx;
  letter-spacing: 5rpx;
  text-align: center;
  border-radius: 150rpx;
  color: #fff;
  /* left: 50%;
  transform: translateX(-50%); */
  margin: 0 auto;
  margin-top: 20rpx;
}
.add1{
  background-color: rgb(63, 187, 224);
}
.add2{
  background-color: rgb(37, 38, 39);
}

/* 选择动画 */
#choose{
  width: 550rpx;
  height: 550rpx;
  position: fixed;
  /* background: rgba(37, 33, 33, 0.411); */
  /* top: 50%;
  left: 50%;
  transform: translate(-50%,-50%); */
  top:300rpx;
  left: 100rpx;
   z-index: 20;
  
}
#choose .circle{
  position: absolute;
  width: 550rpx;
  height: 550rpx;
  border-radius: 300rpx;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  border: 2px solid rgba(248, 247, 247, 0.664);
}
#choose ul li{
  width: 150rpx;
  display:inline-block;
  height: 150rpx;
  background-color: rgb(60, 153, 182);
  list-style: none;
  position: absolute;
  color: #fff;
  letter-spacing: 4rpx;
  border-radius: 100rpx;
}
#choose ul li span{
  display: block;
  position: absolute;
  width: 70rpx;
  height: 70rpx;
  font-size: 28rpx;
  text-align: center;
  top: 50%;
  left: 51%;
  transform: translate(-50%,-50%);
}
#choose ul li:nth-child(1){
  left: 0;
  top: 0;
  background: rgb(201, 75, 75);
}
#choose ul li:nth-child(2){
  right: 0;
  top: 0;
  background: rgba(205, 82, 221, 0.918);
}
#choose ul li:nth-child(3){
  left: 0;
  bottom: 0;
  background: rgb(69, 202, 180);
}
#choose ul li:nth-child(4){
  right: 0;
  bottom: 0;
  background: rgb(230, 202, 44);
}

.decition{
  width: 220rpx;
  height: 220rpx;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  border-radius: 120rpx;
  text-align: center;
  font-weight: 600;
  color: #fff
}
.decition1{
  font-size: 28rpx;
  letter-spacing: 2rpx;
  background: rgba(37, 33, 33, 0.411);
}
.decition2{
  font-size: 32rpx;
  letter-spacing: 4rpx;
  background: rgba(23, 204, 92, 0.726);
}
.decition span{
  display: block;
  position: absolute;
  width: 160rpx;

  text-align: center;
  top: 50%;
  left: 51%;
  transform: translate(-50%,-50%);
}


.choose1{
  display: none;
}
.choose2{
  display: block;
  animation: myMove1 2.5s ease;
}
.choose3{
  display: block;
  animation: myMove2 2.5s ease;
}
.choose4{
  display: block;
  animation: myMove3 2.5s ease ;
}
.choose5{
  display: block;
  animation: myMove4 2.5s ease ;
}

@keyframes myMove1 {
  0% {
    transform: translate(250rpx,1000rpx);

  }
  100% {
    transform: translate(0,0);
 
  }
}
@keyframes myMove2 {
  0% {
    transform: translate(-250rpx,1000rpx);
  }
  100% {
    transform: translate(0,0);
  }
}
@keyframes myMove3 {
  0% {
    transform: translate(250rpx,600rpx);
  }
  100% {
    transform: translate(0,0);
  }
}
@keyframes myMove4 {
  0% {
    transform: translate(-250rpx,600rpx);
  }
  100% {
    transform: translate(0,0);
  }
}
/* 按钮波纹特效 */
.ripple1{
  width: 112%;
  height: 112%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  border-radius: 100rpx;
  opacity: 0;
}
  
.ripple2{
  width: 130%;
  height: 130%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  /* border: 1px solid #fff; */
  border-radius: 100rpx;
  /* animation: ripples2 2.5s infinite ; */
  opacity: 0;
}
.ri11{
  border: 1px solid rgb(201, 75, 75);
  animation: ripples1 2.5s infinite 2.5s;
}
.ri12{
  border: 1px solid rgba(205, 82, 221, 0.918);
  animation: ripples1 2.5s infinite 3.5s;
}
.ri13{
  border: 1px solid rgb(69, 202, 180);
  animation: ripples1 2.5s infinite 4s;
}
.ri14{
  border: 1px solid rgb(230, 202, 44);
  animation: ripples1 2.5s infinite 3s;
}
.ri21{
  animation: ripples2 2.5s infinite 2.5s;
  border: 1px solid rgb(201, 75, 75);
}
.ri22{
  animation: ripples2 2.5s infinite 3.5s;
  border: 1px solid rgba(205, 82, 221, 0.918)
}
.ri23{
  animation: ripples2 2.5s infinite 4s;
  border: 1px solid rgb(69, 202, 180)
}
.ri24{
  animation: ripples2 2.5s infinite 3s;
  border: 1px solid rgb(230, 202, 44)
}


@keyframes ripples1 {
  0% {
    opacity: 0;
  }
  60% {
    opacity: 1;
  }
  80% {
    opacity: 1;
  }
  100%{
    opacity: 0;
  }
}
@keyframes ripples2 {
  0% {
    opacity: 0;
  }
  20% {
    opacity: 0;
  }
  80%{
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
#choose .tip{
  position: absolute;
  color: #fff;
  font-size: 24rpx;
  letter-spacing: 2rpx;
  left: 50%;
  transform: translateX(-50%);
  top: 390rpx;
  width: 300rpx;
  text-align: center;
  opacity: 1;
  animation: tipChange 4s  ;
}
@keyframes tipChange{
  0% {
    opacity: 0;
  }
  70%{
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
#choose image{
  width: 100%;
  height: 80%;
  position: absolute;
  top: 10%;
  z-index: 15;
}

/* 掩盖层 */
.cover{
  position: fixed;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.719);
  z-index: 10;
  top: 0;
}

</style>
