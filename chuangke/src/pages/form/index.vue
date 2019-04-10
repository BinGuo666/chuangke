<template>
 <div>
   <!-- 头部组件 -->
<news></news>

<!-- 申请表单 -->
<div id="form"   >
   
   <div class="form_title">
     <span>填写个人资料</span> 
   </div>
   
   <div class="form_text1">
       <ul>
         <li class="userId">
           <div class="text_box"> &nbsp;学&nbsp;号<input @input="testId" type="number" v-model="userId" placeholder="请输入学号" :disabled="opening"></div>
           <div class="test" v-if="test[0]"><image src="../../static/images/false.png" alt=""/>请输入正确的学号</div>
         </li>
         <li class="userName">
           <div class="text_box">&nbsp;姓&nbsp;名<input @input="testName" type="text" v-model="userName" placeholder="请输入姓名" :disabled="opening"></div>
           <div class="test" v-if="test[1]"><image src="../../static/images/false.png" alt=""/>请输入正确的姓名</div>
           </li>
         <li class="userPhone">
           <div class="text_box">联系电话<input @input="testPhone" type="number" v-model="userPhone" placeholder="请输入联系电话" :disabled="opening"></div>
           <div class="test" v-if="test[2]"><image  src="../../static/images/false.png" alt=""/>电话格式错误</div>
           </li>
         <li class="userMail" >
           <div class="text_box">&nbsp;邮&nbsp;箱<input @input="testMail" type="text" v-model="userMail" placeholder="请输入邮箱" :disabled="opening"></div>
           <div class="test" v-if="test[3]"><image src="../../static/images/false.png" alt=""/>邮箱格式错误</div>
         </li>
       </ul>
      <!-- {{userId}} -->
   </div>
<!-- 性别 -->

<div class="form_sex">
  <div class="sex_box">性&nbsp;别</div>
  <div class="sex_select">
    <input name="sex" type="radio"  @click="checkSex = true" :checked="checkSex"/>男   
    &nbsp;&nbsp;&nbsp;
    <input name="sex" type="radio"  @click="checkSex = false" :checked="!checkSex" />女
  </div>
</div>  
<!-- 年级专业 -->
<div class="form_grade"  >
   <div class="grade_box">
     年级专业
   </div>
 <div class="mpvue-picer" >
    <div class="picker_box" @click="showPicker" >
      {{userGradedate}}</div>
      <div @error="grade_blur">
<mpvue-picker   ref="mpvuePicker" :mode="mode" :pickerValueDefault="pickerValueDefault" @onChange="onChange" @onConfirm="onConfirm" @onCancel="onCancel" :pickerValueArray="pickerValueArray"></mpvue-picker>
      </div>
    
  </div> 
</div>

<!-- 已选方向 -->
<div class="form_choose" >
   已选方向
   <span>{{select1}}&nbsp;{{select2}}</span>
</div>
<!-- 个人简介 -->

<div class="form_summary" v-show="pickshow">
  <div class="form_title">
     <span>个人介绍</span> 
   </div>
<textarea style="z-index:2" class='suggest_text' @input="bindText1" v-model="userSummary" maxlength='200' placeholder='你的兴趣爱好，学习方法、参加社团情况等...' >

<text>{{t1_length}}/200</text> 
</textarea>
</div>

<!-- 个人技能 -->
<div class="form_summary" v-show="pickshow">
  <div class="form_title">
     <span>技能掌握情况</span> 
   </div>
<textarea class='suggest_text' @input="bindText2" v-model="userKnowledge" maxlength='200' placeholder='对该方向的认识，和对技能的掌握情况...' >

<text>{{t2_length}}/200</text> 
</textarea>
</div>


<button id='submit' @click="submit()">提交申请</button>
</div>
<div class="footer_tip">
如无法跳转下载报名表链接，请直接在浏览器访问https://binguo.online/1.docx
</div>
<footers></footers>
 </div>
</template>

<script>
import footers from "@/components/footer";
import news from "@/components/new";
import mpvuePicker from 'mpvue-picker';
 export default {
   data () {
     return {
       opening:false,
       select1:'',
       select2:'',
       selects:[],
       userId:'',
       userName:'',
       userPhone:'',
       userSex:'',
       userMail:'',
       userChoose:'',
       userMajor:'',
       userGrade:'',
       userSummary:'',
       userKnowledge:'',
       checkSex:false,
       pickshow:true,
       date:'',
       userGradedate:'请选择你的年级专业',
       test:[false,false,false,false],
       mode: 'multiLinkageSelector',
       t1_length:"0",
       t2_length:"0",
      pickerValueArray: [
  {
    label: '2017级',
    value: 0,
    children: [{
      label: '非计算机专业',
      value: 1
    },
    {
      label: '计算机科学',
      value: 2
    },
    {
      label: '软件工程',
      value: 3
    },
    {
      label: '物联网',
      value: 4
    },
    {
      label: '智能科学与技术',
      value: 5
    },
    {
      label: '数据科学与大数据',
      value: 6
    },
    {
      label: '信息管理与信息系统',
      value: 7
    },
    ]
  },
  {
    label: '2018级',
    value: 1,
    children: [{
      label: '非计算机专业',
      value: 1
    },
    {
      label: '计算机科学',
      value: 2
    },
    {
      label: '软件工程',
      value: 3
    },
    {
      label: '物联网',
      value: 4
    },
    {
      label: '智能科学与技术',
      value: 5
    },
    {
      label: '数据科学与大数据',
      value: 6
    },
    {
      label: '信息管理与信息系统',
      value: 7
    }
    ]
  }
],
      pickerValueDefault: [1]
     }
   },
   components: {
       footers,
       news,
       mpvuePicker
   },
   methods:{
    getit(){
      // wx.request({
      //   url: `http://localhost:3000/users/chuangke`,
      //   data: {"userId":'123546'},
      //   method: "POST",
      //   header: {
      //     "content-type": "application/json"
      //   },
      //   success(res) {
      //     // console.log(res.data);
          
      //   }
      // });


    wx.request({
        url: `http://localhost:3000/users/chuangke/download`,
        data: {"userId":'123546'},
        method: "GET",
        header: {
          "content-type": "application/json"
        },
        success(res) {
          // console.log(res.data);
          
        }
      });

    },
    showPicker() {
      this.pickshow = false;
      this.$refs.mpvuePicker.show();
  
    },
    onChange(e) {
      this.userGradedate = e.label;
      this.userGrade = this.pickerValueArray[e.value[0]].label;
      this.userMajor = this.pickerValueArray[e.value[0]].children[e.value[1]-1].label;
      console.log(this.userMajor);
      console.log(this.userGrade);
  
      
    },
    onConfirm() {
      
      this.pickshow = true;

    },
    onCancel() {
      this.pickshow = true; 
    },
    
     bindText1 () {
      this.t1_length= this.userSummary.length
     },
     bindText2 () {
      this.t2_length= this.userKnowledge.length
     },
     testId(){
        let reg = new RegExp("^[2][0][1][6,7,8][0-9]{8}$");
      if(!reg.test(this.userId)){
        this.test[0] = true;
      }else{
        this.test[0] = false;
      }
     },
     testName(){
       let reg = new RegExp("^[\u4e00-\u9fa5]{2,4}$");
      if(!reg.test(this.userName)){
        this.test[1] = true;
      }else{
        this.test[1] = false;
      }
     },
     testMail(){
       let reg = new RegExp("^[a-z0-9]+([._\\-]*[a-z0-9])*@([a-z0-9]+[-a-z0-9]*[a-z0-9]+.){1,63}[a-z0-9]+$");
      if(!reg.test(this.userMail)){
        this.test[3] = true;
      }else{
        this.test[3] = false;
      }
     },
     testPhone(){
       let reg = new RegExp("^[1][3,4,5,7,8][0-9]{9}$");
      if(!reg.test(this.userPhone)){
        this.test[2] = true;
      }else{
        this.test[2] = false;
      }
     },
     grade_blur(){
       console.log("事件1");
     },
     grade_focus(){
       console.log("事件2");
     },
     submit(){
      
       this.userChoose = this.select1+' '+this.select2;
       this.userSex = this.checkSex? '男':'女';
       let that = this;
       let getit = true;
       let usernews = {
         userId:this.userId==''?getit=false:this.userId,
         userName:this.userName==''?getit=false:this.userName,
         userGrade:this.userGrade==''?getit=false:this.userGrade,
         userMajor:this.userMajor==''?getit=false:this.userMajor,
         userPhone:this.userPhone==''?getit=false:this.userPhone,
         userSex:this.userSex==''?getit=false:this.userSex,
         userMail:this.userMail==''?getit=false:this.userMail,
         userSummary:this.userSummary==''?getit=false:this.userSummary,
         userChoose:this.userChoose==''?getit=false:this.userChoose,
         userKnowledge:this.userKnowledge==''?getit=false:this.userKnowledge
       }
       this.test.forEach(item => {
         if(item==true){
           getit = false
         }
       });
       console.log(getit);
       if(getit ==true){
         wx.request({
        url: `https://binguo.online/users/chuangke`,
        data: usernews,
        method: "POST",
        header: {
          "content-type": "application/json"
        },
        success(res) {
          let urls = 'https://binguo.online/word/'+that.userId+'.docx'
                  wx.showToast({
                    title: '申请成功！',
                    icon: 'success',
                    duration: 2000
                   })    ,
                   setTimeout(function(){
                                wx.downloadFile({
                            url: urls, 
                            success(res) {
                            console.log(urls);
                              if (res.statusCode === 200) {
                                var filePath = res.tempFilePath 
                                  wx.openDocument({
                                    filePath: filePath,
                                    success: function (res) {
                                      console.log('打开文档成功')
                                    }
                                  })
                              }
                            }
                          })
                   },1000);
                  
          
            }
         });
       }else{
         
         wx.showToast({
                    title: '请认真核实表单是否填写完整！',
                    icon: 'none',
                    duration: 2000
                   })   
       }
     }
    
   },
   onShow(){
      var pages = getCurrentPages();
      console.log(pages);
       this.pickshow = true;
      this.select1 = pages[1].options.select1;
      this.select2 = pages[1].options.select2=="undefined"? '':pages[1].options.select2;
   },
  onHide(){
    console.log("隐藏")
    this.select1 = '',
    this.select2 = ''
  },
  onUnload(){
    console.log("onunload2")
  }
 }
</script>

<style>
#form{
  width: 88%;
  position: relative;
  margin-left: 6%;
  
}
#form .form_title{
  width: 100%;
  height: 30rpx;
  border-left: 6rpx solid rgb(33, 175, 241);
  margin: 30rpx 0 40rpx 0;
  position: relative;
 
   left: -20rpx;

  /* background: #000; */

}
.form_title span{
  font-size: 34rpx;
  width: 100%;
  height: 100%;
  letter-spacing: 2rpx;
  line-height: 30rpx;
  margin-left: 15rpx;
  display: block;
  font-weight: 700;
}
.form_text1{
  width: 100%;
  position: relative;
  height: 440rpx;
}
.form_text1 ul li{
  list-style: none;
  width: 100%;
  height: 100rpx;
  margin-top: 10rpx;
  font-size: 36rpx;
  letter-spacing: 2rpx;
  float: left;
  position: relative;
  letter-spacing: 4rpx;
}
.form_text1 .text_box{
  width: 100%;
  height: 50rpx;
  position: relative;
  border-bottom: 1rpx solid rgba(11, 75, 160, 0.568);
  font-size: 34rpx;
  color: rgba(53, 52, 52, 0.801);
  padding-bottom: 5rpx;
  line-height: 50rpx;
}
.form_text1 ul li input{
  width: 75%;
  height: 40rpx;
  position: relative;
  float:right;
  color: black;
  font-size: 32rpx;
  
}
.form_text1 ul li .test image{
  position: relative;
  float: left;
  width: 32rpx;
  height: 32rpx;
  margin-right: 6rpx;
  margin-top: 3rpx;
}
.form_text1 ul li .test{
   position: absolute;
   color: red;
   bottom: 10rpx;
   left: 20%;
   font-size: 26rpx;
}
.form_sex{
  width: 100%;
  height: 100rpx;
  /* background-color: rgba(53, 50, 50, 0.555); */
  position: relative;
  font-size: 34rpx;
  line-height: 80rpx;
  letter-spacing: 4rpx;
  float: left;
}
.form_sex .sex_box{
  float: left;
  position: relative;
  margin-left: 10rpx;
}
.form_sex .sex_select{
  position: absolute;
  left: 35%;
}
.form_grade{
  position: relative;
  float: left;
  width: 100%;
  /* background: rgba(0, 0, 0, 0.473); */
  height: 120rpx;
  z-index: 10;
}
.grade_box{
  letter-spacing: 4rpx;
  font-size: 34rpx;
  float: left;
  line-height: 120rpx;
}
.mpvue-picer{
  width: 70%;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 25%;
  font-size: 34rpx;
  text-align: center;
  letter-spacing: 4rpx;
  line-height: 120rpx;
  height: 100rpx;
  color: rgb(56, 56, 56);
  text-align: center
}
.mpvue-picer mpvue-picker{
  z-index: 100
}
/* 个人方向 */
.form_choose{
  position: relative;
  width: 100%;
  height: 120rpx;
  font-size: 34rpx;
  line-height: 60rpx;
  float: left;
  letter-spacing: 4rpx;
  margin-bottom: 20rpx;
  line-height: 120rpx;
}
.form_choose span{
  display: block;
  position: absolute;
  left: 25%;
  top: 0;
  width: 70%;
  height: 60rpx;
  text-align: center;
  color: rgba(153, 153, 153, 0.644);
}


/* 个人介绍和知识掌握样式 */
.form_summary .form_title{
    width: 100%;
  height: 40rpx;
  border-left: 8rpx solid rgb(33, 175, 241);
  position: relative;
  left: -20rpx;
  margin-bottom: 20rpx;
}
.form_summary .form_title span{
  font-size: 34rpx;
  width: 100%;
  height: 100%;
  letter-spacing: 2rpx;
  line-height: 30rpx;
  margin-left: 15rpx;
  display: block;
  font-weight: 700;
}
.form_summary{
   width: 100%;
  position: relative;
  float: left;
  z-index: 3;
}

.suggest_text{
  width: 90%;
  margin-left: 5%;
  height: 200rpx;
  overflow: hidden;
  font-size: 32rpx;
  padding-bottom: 25rpx;
  position: relative;
  border: 1rpx solid #999;
  margin-bottom: 30rpx;
  margin-top: 30rpx;
  display: block;
  z-index: 1;
}
.suggest_text text{
  position: absolute;
  bottom: 0;
  right: 10rpx;
  display: block;
  color: #999;
}

/* 提交按钮 */
#submit{
  position: relative;
  width: 60%;
  margin-left: 20%;
  background: rgb(29, 201, 52);
  color: #fff;
  top: 20rpx;
  letter-spacing: 2rpx;
  display: block;
  margin-bottom: 30rpx;
}
.footer_tip{
  font-size: 28rpx;
  color: rgba(153, 153, 153, 0.603);
  width: 90%;
  position: relative;
  text-align: center;
  margin-left: 5%;
}
</style>
