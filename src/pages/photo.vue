<template>
  <div>
    <div class="card1 col-12">
      <card>
        <div class="row col-12" style="padding-top: 5px">
          <p class="ml-3" style="font-size: 19px">窗位:</p>
          <div class="col-4">
            <slider
              vertical
              class="mt-3"
              type="info"
              value="number"
              :options="{ step: 1 }"
              v-model="tmpvalue1"
              :range="{ min: 0, max: 1000 }"
            ></slider>

            <div class="mt-3">{{ sliderValue1 }}</div>
          </div>
          <p style="margin-left: 115px; font-size: 19px">窗宽:</p>
          <div class="col-4">
            <slider
              class="mt-3"
              type="info"
              value="number"
              :options="{ step: 1 }"
              v-model="tmpvalue2"
              :range="{ min: 0, max: 1000 }"
            ></slider>

            <div class="mt-3">{{ sliderValue2 }}</div>
          </div>
          <div>
            <base-button
              type="info"
              class="animation-on-hover ml-4"
              @click="deal"
              style="width: 90px; height: 35px"
              ><h4
                style="
                  margin-top: 10px;
                  writing-mode: vertical-lr;
                  color: #fffffb;
                  justify-content: center;
                "
              >
                确定
              </h4></base-button
            >
          </div>
        </div>
      </card>
    </div>
    <div class="card2">
      <div class="row">
        <card class="photo ml-5">
          <img v-bind:src="pathOrigin" />
          <p class="card-text" style="font-size: 20px; text-align: center">
            原图
          </p>
        </card>
        <card class="photo ml-3">
          <img v-bind:src="pathOrigin" />
          <p class="card-text" style="font-size: 20px; text-align: center">
            窗位处理效果
          </p>
        </card>
      </div>
    </div>
    <div class="photoSlider">
      <slider
        class="mt-3"
        type="info"
        value="number"
        :options="{ step: 1 }"
        v-model="photoSliderValue"
        :range="{ min: this.photoSliderMin, max: this.photoSliderMax }"
      >
      </slider>
      <div class="photoword mt-3">
        <h3>当前为第{{ SliderValue3 }}张图片</h3>
      </div>
    </div>
  </div>
</template>

<script>
import BaseButton from "../components/BaseButton.vue";
import Slider from "../components/Slider.vue";
export default {
  components: {
    BaseButton,
    Slider,
  },
  data() {
    return {
      windowBit: "",
      windowWidth: "",
      tmpvalue1: "",
      tmpvalue2: "",
      photoSliderValue: "1",
    };
  },
  computed: {
    sliderValue1() {
      let ans = Math.trunc(this.tmpvalue1);
      return ans;
    },
    sliderValue2() {
      let ans = Math.trunc(this.tmpvalue2);
      return ans;
    },
    pathOrigin() {
      const thepath = "/static/" + this.SliderValue3 + ".png";
      return thepath;
    },
    photoSliderMin() {
      return 1;
    },
    photoSliderMax() {
      return 10;
    },
    SliderValue3() {
      let ans = Math.trunc(this.photoSliderValue);
      return ans;
    },
  },
  methods: {
    deal() {},
  },
};
</script>

<style>
.card1 {
  margin: auto;
  margin-top: 180px;
  width: 1070px;
}
.card2 {
  margin: 0 auto;
  width: 1100px;
}
.photo {
  height: 550px;
  width: 512px;
  border-radius: 14px;
}
.card-body {
  padding: 5px;
  border-radius: 3px;
}
.photoSlider {
  width: 1000px;
  margin: 0 auto;
}
.photoword {
  text-align: center;
}
.card {
  border-radius: 14px;
  background: rgba(235, 238, 241, 0.01);
  border-radius: 15px;
}
</style>
