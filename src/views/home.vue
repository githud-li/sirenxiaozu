<!--  -->
<template>
  <div>
<van-nav-bar title="时尚花卉" fixed >
  <van-icon  name="qr-invalid" slot="left" @click="fenlei" />
  
</van-nav-bar>

<van-pull-refresh v-model="isLoading"  @refresh="onRefresh">
<div class="com">
<van-search placeholder="请输入搜索关键词" @click="search"/>

    
<van-swipe :autoplay="3000" indicator-color="white" >
  <van-swipe-item><img src="../img/1.jpg" style="width: 100%;height: 200px;"/></van-swipe-item>
  <van-swipe-item><img src="../img/2.jpg" style="width: 100%;height: 200px;" /></van-swipe-item>
  <van-swipe-item><img src="../img/3.jpg" style="width: 100%;height: 200px;"/></van-swipe-item>
  <van-swipe-item><img src="../img/4.jpg" style="width: 100%;height: 200px;"/></van-swipe-item>
</van-swipe>

<van-notice-bar  text="春山流翠半沾衣，红粉间差合一围。频有莺鹂争相语，桃花偏瘦杏花肥。"  left-icon="flower-o"/>

<van-grid :column-num="5" :border='false'>
  <van-grid-item icon="flower-o" text="鲜花" to="/prolist"/>
  <van-grid-item icon="flower-o" text="永生花" to="/prolist#oldflower"/>
  <van-grid-item icon="point-gift-o" text="蛋糕" to="/prolist#cake"/>
  <van-grid-item icon="shop-o" text="礼品" to="/prolist#gifts"/>
  <van-grid-item icon="smile-o" text="巧克力" to="/prolist#chocolate"/>

</van-grid>

<van-divider >一秒选花</van-divider>

<van-grid :border="true" :column-num="3" >
  <van-grid-item to="/prolist">
    <p class="pp">送恋人</p>
    <img src="../img/5.png" style="width: 100px;height: 100px;"/>
  </van-grid-item>
  <van-grid-item to="/prolist#oldflower">
    <p class="pp">送长辈</p>
    <img src="../img/6.png" style="width: 100px;height: 100px;"/>    
  </van-grid-item>
  <van-grid-item to="/prolist">
    <p class="pp">送朋友</p>
    <img src="../img/7.png" style="width: 100px;height: 100px;"/>
  </van-grid-item>
</van-grid>


<van-grid :border="true" :column-num="4" >
  <van-grid-item to="/prolist#cake">
  
    <span style="font-size: 14px; color: #f00">生日祝福</span>
    <img src="../img/8.png" style="width: 60px;height: 60px;"/>
  </van-grid-item>
  <van-grid-item to="/prolist">
    <span style="font-size: 14px; color: #f00">表白求婚</span>
    <img src="../img/9.png" style="width: 60px;height: 60px;"/>    
  </van-grid-item>
  <van-grid-item to="/prolist#oldflower"> 
    <span style="font-size: 14px; color: #f00">开业商务</span>
    <img src="../img/10.png" style="width: 60px;height: 60px;"/>
  </van-grid-item>
  <van-grid-item to="/prolist#oldflower">
    <span style="font-size: 14px; color: #f00">周年纪念</span>
    <img src="../img/11.png" style="width: 60px;height: 60px;"/>
  </van-grid-item>
</van-grid>


<van-grid :border="true" :column-num="3" >
  <van-grid-item to="/prolist">
    <p class="ppp">新品来袭</p>
    <img src="../img/12.png" style="width: 100px;height: 100px;"/>
  </van-grid-item>
  <van-grid-item to="/prolist#oldflower">
    <p class="ppp">品味之选</p>
    <img src="../img/13.png" style="width: 100px;height: 100px;"/>    
  </van-grid-item>
  <van-grid-item to="/prolist#oldflower">
    <p class="ppp">设计师臻选</p>
    <img src="../img/14.png" style="width: 100px;height: 100px;"/>
  </van-grid-item>
</van-grid>



<van-divider>送恋人/爱情鲜花</van-divider>
<van-card v-for="(item,i) in lists" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions" :title="item.name" :thumb="item.coverImg" @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>


<van-divider>送长辈鲜花</van-divider>
<van-card v-for="(item1,i) in list1" :key="i" :num="item1.quantity"  :price="item1.price"  :desc="item1.descriptions"    :title="item1.name" :thumb="item1.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>



<van-divider>永生花</van-divider>
<van-card v-for="(item,i) in list2" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions"    :title="item.name" :thumb="item.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>



<van-divider>蛋糕</van-divider>
<van-card v-for="(item,i) in list3" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions"    :title="item.name" :thumb="item.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>


<van-divider>礼品</van-divider>
<van-card v-for="(item,i) in list4" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions"    :title="item.name" :thumb="item.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>



<van-divider>巧克力</van-divider>
<van-card v-for="(item,i) in list5" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions"    :title="item.name" :thumb="item.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>

<van-divider>巧克力</van-divider>
<van-card v-for="(item,i) in list6" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions"    :title="item.name" :thumb="item.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>

<van-divider>巧克力</van-divider>
<van-card v-for="(item,i) in list7" :key="i" :num="item.quantity"  :price="item.price"  :desc="item.descriptions"    :title="item.name" :thumb="item.coverImg"  @click="detail(item._id)"/>
<van-divider dashed><van-button   size="small">查看更多</van-button></van-divider>


<img src="../img/15.png" style="width: 100%;height: 150px;" />


<van-divider dashed>
  Copyright © 2017~2019 时尚花卉 版权所有<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;中国鲜花网领先品牌，鲜花速递专家！<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;郑州市时尚花卉信息技术有限公司
</van-divider>





  </div>  
    </van-pull-refresh>
   

  </div>
</template>

<script>
import axios from "axios";
export default {
  data () {
    return {
      isLoading: false,
      lists:'',
      list1: "",
      list2: "",
      list3: "",
      list4: "",
      list5: "",
      list6: "",
      list7: "",
      xianhua: "5d8b05a4fe04943d5e5402d1",//鲜花
      shangwuxianhua:'5d8b07effe04943d5e5402d3',//商务鲜花
      yongshenghua:'5d8b08bcfe04943d5e5402d4',//永生花
      dangao:'5d8b091efe04943d5e5402d5',//蛋糕
      qiaokeli:'5d8b0981fe04943d5e5402d6',//巧克力
      teseliping:'5d8b0ad0fe04943d5e5402d7',//特色礼品
      gongzai:'5d8b0b82fe04943d5e5402d8',//品牌公仔
      lilan:'5d8b0bfdfe04943d5e5402d9'//礼篮
    };
  },
  mounted(){
    let params = {
      per:2000,
    }
    let url1 =`http://api.cat-shop.penkuoer.com/api/v1/products`
    
    this.$axios.get(url1,{params:params}).then((data) => {
      console.log(data)
      this.list=data.data.products
      console.log(this.list)
      //过滤
        this.list = this.list.filter(
                  v => v.name.indexOf('时尚花卉') !== -1
              )      
        console.log(this.list)
        this.list = this.list.map(v => {
           v.name = v.name.slice(5)
            return v
        })
        this.lists = this.list.filter(
        v => v.productCategory == this.xianhua//鲜花
      )
         this.list1 = this.list.filter(
        v => v.productCategory == this.shangwuxianhua//商务鲜花
      )
        this.list2 = this.list.filter(
        v => v.productCategory == this.yongshenghua//永生花
      )
       this.list3 = this.list.filter(
        v => v.productCategory == this.dangao//蛋糕
      )
       this.list4 = this.list.filter(
        v => v.productCategory == this.qiaokeli//巧克力
      )
       this.list5 = this.list.filter(
        v => v.productCategory == this.teseliping//特色礼品
      )
       this.list6 = this.list.filter(
        v => v.productCategory == this.gongzai//品牌公仔
      )
       this.list7 = this.list.filter(
        v => v.productCategory == this.lilan//礼篮
      )
    })
  },
  methods:{
    detail(id){
      console.log(id)
      this.$router.push('/details'+id)
    },
    onRefresh(){
      setTimeout(() => {
        this.$toast('刷新成功');
        this.isLoading = false;
      }, 500);
    },
    fenlei(){//分类
      this.$router.push('/fenlei')
    },
   search(){//搜索
      this.$router.push('/search')
    },
    // flowers(){//鲜花
    //   this.$router.push('/flowers')
    // },
    Everlasting(){//永生花
      this.$router.push('/Everlasting')
    },
    cake(){//蛋糕
      this.$router.push('/cake')
    },
    gift(){//礼品
      this.$router.push('/gift')
    },
    chocolate(){//巧克力
      this.$router.push("/chocolate")
    }
  }
}

</script>
<style  scoped>
.com{
  margin-top: 46px;
  margin-bottom: 50px
 
}
.van-grid{
  position: relative;
}
.van-grid .pp{
  position: absolute;
  top: 82px;
  font-size: 14px;
  color: #fff
}
.van-grid .ppp{
  position: absolute;
  top: 83px;
  font-size: 14px;
  color: #000
}
</style>