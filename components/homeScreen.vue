<template>
  <view class="container">
    
  </view>
</template>
<script>
// import { NativeModules } from 'react-native';
// var RNHyperTrack = NativeModules.RNHyperTrack;
import testData from "../halfcuteTestData";

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
    },
    inithypertrack: async function() {
      try {
        await RNHyperTrack.initialize('IQfY5HB-JH1OKXtGlYmm4Bkp-1z-iDDmyffKPo-kYvsEoZbdpEQwQ-eUb1ChRkugPYVSdmxFN-b5c7LmJY5ovw', true)
        RNHyperTrack.setDevice('Anil', {});
        this.hypertrackKey = await RNHyperTrack.isTracking();
      } catch (error) {
        this.hypertrackKey = 'error'
      }
    },
    disablehypertrack: async function() {
      try {
        await RNHyperTrack.stopTracking();
        this.hypertrackKey = await RNHyperTrack.isTracking();
        console.log('stopped');
      } catch (error) {
         this.hypertrackKey = 'error'
      }
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
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.buttonStyle {
  width: 100%;
}
.text-color-primary {
  color: blue;
}
</style>
