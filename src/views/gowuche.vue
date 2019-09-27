<!-- 购物车 -->
<template>
  <div>
    <van-nav-bar left-arrow title="购物车" @click-left="onClickLeft" />
    <div>

    <van-swipe-cell v-for="(item,i) in goods" :key="i"> 
      <!-- <van-cell :border="true" title="单元格" value="内容" /> -->
    <van-card 
      :num="item.product.quantity"
      :price="item.product.price"
      :desc="item.product.descriptions"  
      :title="item.product.name"
      :thumb="item.product.coverImg"
      :value="'￥'+item.product.price*value+'*'+item.product.quantity"/>
      <template slot="right">
        <van-button square type="danger" text="删除" @click="btn(item._id)" />
      </template>
    </van-swipe-cell>




    <van-submit-bar
  :price="formatPrice()"
  button-text="提交订单"
  @submit="onSubmit"
/>










    </div>

     
    <div class="more">购买该商品的还购买了</div>
    <van-grid>
      <van-grid-item icon="photo-o" text="文字" :key="i" v-for="i in 4">
        <van-image src="https://img.yzcdn.cn/vant/apple-2.jpg" />
        <span>永生花带灯</span>
        <span class="morePrice">￥398</span>
      </van-grid-item>
    </van-grid>
  </div>
</template>


<script>
export default {
   data() {
    return {
       value: "1",
      goods: [
      ],

    };
  },
  mounted () {
    let url =`http://api.cat-shop.penkuoer.com/api/v1/shop_carts`
    let token =localStorage.getItem('token')
    this.$axios.get(url,{
        headers:{Authorization: 'Bearer ' +token}
      }).then((res)=>{
      console.log(res.data)
 
      this.goods=res.data.slice(3)
      console.log(this.goods)
    
    })    
  },
  computed: {
    //计算属性
  },

  methods: {
    onClickLeft(){
      this.$router.go(-1)
    },
    onSubmit(){
      this.$router.push('/cartsubmit')
    },
    formatPrice() {
      let sum = 0;
      for (let i = 0; i < this.list; i++) {
        var num = Number(this.list[i].pprice*this.list[i].pnum);
        console.log(num);
        sum += num * 100;
      }
      return sum;
    },
    btn(_id) {
      console.log(_id)
      let url =`http://api.cat-shop.penkuoer.com/api/v1/shop_carts/${_id}`
      let token = localStorage.getItem('token')
      // console.log(url)
      this.$axios.delete(url,{
        headers:{Authorization: 'Bearer ' +token}
      }).then((res)=>{
        console.log(res.status)
        if(res.status == 200){
          alert('删除成功')
          Location.reload()
        }else{
          alert('删除失败')
          this.$router.push('/login')
        }
    })
    }
    
}
}
</script>
<style  scoped>
.card-goods {
  padding: 10px 0;
  background-color: #fff;
}
.card-goods__item {
  position: relative;
  background-color: #fafafa;
}

/* .van-checkbox__label {
  width: 100%;
  height: auto;
  padding: 0 10px 0 15px;
  box-sizing: border-box;
} */

.van-checkbox__icon {
  top: 50%;
  left: 10px;
  z-index: 1;
  position: absolute;
  margin-top: -10px;
}

.van-card__price {
  color: #f44;
  font-size: 18px;
  position: absolute;
  bottom: 0;
}
.van-submit-bar {
  bottom: 50px;
}

.van-stepper {
  display: inline-block;
  position: absolute;
  bottom: 40px;
  right: 70px;
}
#del {
  display: inline-block;
  position: absolute;
  bottom: 40px;
  right: 5px;
}
.more {
  padding-left: 27px;
  font-size: 12px;
  color: #ff551a;
}
.van-grid-item .van-image {
  width: 54px;
  height: 54px;
}
.van-grid-item span {
  font-size: 10px;
  line-height: 18px;
}
.morePrice {
  color: #ff551a;
}
</style>