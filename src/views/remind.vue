<!-- 生日提醒/添加提醒 -->
<template>
  <div>
    <van-nav-bar title="添加提醒"  left-arrow @click-left="tixing"></van-nav-bar>

    <van-tabs type="card" animated>
        <van-tab title="标签 1" >
          <van-cell-group>
            <van-field clearable  label="姓名"  placeholder="请输入用户名" />
            <van-nav-bar  left-text="性别"  style="color:#000">
              <van-icon slot="title">
                <van-radio-group v-model="radio">
                  <van-radio  name="1"  checked-color='#000'  style="float:left">男</van-radio>
                  <van-radio  name="2"  checked-color='#000'  style="float:left;margin-left:60px">女</van-radio>
                </van-radio-group>
              </van-icon>
            </van-nav-bar>
            <van-field  v-model="phone"  label="生日"  :placeholder=date  @focus="settime"></van-field>
            <van-field clearable  label="提醒"  placeholder="" />
            <van-field clearable  label="备注"  placeholder="预定餐厅，购买礼物等" />
          </van-cell-group>
          <van-button type="primary" size="large" color="#ffd700">保存</van-button>
        </van-tab>





        <van-tab title="标签 2">
          <van-cell-group>
            <van-field clearable  label="姓名"  placeholder="请输入用户名" />
            <van-nav-bar  left-text="性别"  style="color:#000">
              <van-icon slot="title">
                <van-radio-group v-model="radio">
                  <van-radio  name="1"  checked-color='#000'  style="float:left">男</van-radio>
                  <van-radio  name="2"  checked-color='#000'  style="float:left;margin-left:60px">女</van-radio>
                </van-radio-group>
              </van-icon>
            </van-nav-bar>
            <van-field  v-model="phone"  label="生日"  :placeholder=date  @focus="settime" ></van-field>
            <van-field clearable  label="提醒"  placeholder="" />
            <van-field clearable  label="备注"  placeholder="预定餐厅，购买礼物等" />
          </van-cell-group>
          <van-button type="primary" size="large" color="#ffd700">保存</van-button> 
        </van-tab>
    </van-tabs>

    
    <van-popup    v-model="show"  position="bottom"  :style="{ height: '40%' ,width:'100%'}">
      <van-datetime-picker  v-model="currentDate"  type="date"  @confirm="admit"  @cancel="cancel" :max-date="maxDate" />
            </van-popup>


  </div>
</template>

<script>
export default {
  data () {
    return {
        radio: '1',
        phone:'',
        currentDate: new Date(),
      show: false, date: '2008.08.08',
      maxDate: new Date(3990, 10, 1),
    };
  },
  methods:{
    tixing(){
        this.$router.go(-1)
    },
    save() {
      console.log(5555)
    },
    showPopup() {
      this.show = true;
    },
    settime() {
      this.show = true;
    },
    admit() {
      this.show = false;
      console.log(this.currentDate.toLocaleDateString())
      this.date = this.currentDate.toLocaleDateString()
    }, cancel() {
      this.show = false;
    }
  },
  
}

</script>
<style  scoped>
.van-button--large {
    width: 85%;
    height: 45px;
    line-height: 45px;
    margin-left: 27px;
    margin-top: 23px;
}
.van-tabs--card {
    padding-top: 10px;
}
</style>