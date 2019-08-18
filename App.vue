<template>
  <view class="container">
    <view class="header">
      <view class="statusbar"></view>
      <text class="head-text">HalfCute</text>
    </view>
    <scroll-view :style="{ width: '98%' }">
      <view class="card" v-for="order in Orders" :key="order.id">
        <view class="card-head"></view>
        
        <touchable-opacity class="card-container" :on-press="selectCake(cake)">
          <view class="card-heading">
            <view>
              <text class="font-bold ID-font">{{order.id}}</text>
              <text>{{order.status}}</text>
            </view>
            <view>
              <text>{{order.provider_data.name}}</text>
              <text>{{order.provider_data.contact}}</text>
            </view>
          </view>
          <view class="product-list" v-for="product in order.products" :key="product.product_id">
            <image
              :style="{width: 66, height: 58}"
              :source="{uri: product.image}"
            />
            <text class="product-name">{{product.display_name}}</text>
          </view>
        </touchable-opacity>
      </view>
    </scroll-view>
  </view>
</template>
<script>
import testData from "./halfcuteTestData";
import Communications from 'react-native-communications';
// import { NativeModules } from 'react-native';
// var RNHyperTrack = NativeModules.RNHyperTrack;

export default {
  // props: {
  //   navigation: {
  //     type: Object
  //   }
  // },
  data: function () {
    return {
      hypertrackKey: false,
      Orders: []
    }
  },
  methods: {
    selectCake (cake) {
      // this.navigation.navigate("Details", params = { cake: cake });
    }
  },
  created () {
    testData.getHalfCuteTestData(data => {
      this.Orders = data
    })
    // this.hypertrackKey = 'created'
    // await RNHyperTrack.initialize('IQfY5HB-JH1OKXtGlYmm4Bkp-1z-iDDmyffKPo-kYvsEoZbdpEQwQ-eUb1ChRkugPYVSdmxFN-b5c7LmJY5ovw',true)
    // .then((res) => {
    //   this.hypertrackKey = 'success'
    // })
    // .catch((err) => {
    //   this.hypertrackKey = 'error'
    // })
  }
}
</script>
<style>
.statusbar {
  height: 20px;
  background-color: coral;
}
.card-heading {
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}
.ID-font{
  font-size: 20px;
}
.font-bold {
  font-weight: 900;
}
.product-list{
  width: 98%;
  border-bottom-width: 1;
  border-color: gray;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}
.card{
  margin: 2;
  border-width: 1;
  border-color: gray;
  /* box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2); */
  border-radius: 10;
}
.card-container{
  padding: 15;
}
.card-head {
  border-top-left-radius: 10;
  border-top-right-radius: 10;
  background-color: blue;
  margin-top: 0px;
  height: 15;
}
.head-text {
  font-size: 20;
  color: white;
  padding-left: 5;
  padding-right: 5;
  width: 100%;
}
.header {
  background-color: coral;
  width: 100%;
  height: 60px;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  width:100%;
  flex: 1;
}
</style>
