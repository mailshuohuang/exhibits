<template>
  <div class="w-100 d-flex align-items-stretch flex-column text-white">
    <div style="height: 120px">
      <hr class="mt-4 mb-0 step-line">
      <el-row class="translate-step-group">
        <el-col :span="8" class="step-group d-flex flex-column align-items-center">
          <div class="el-icon-odometer text-white mb-3"></div>
          <div class="w-100 mb-3 text-regular text-truncate">1 小时告警数</div>
          <div class="font-spiral">4</div>
        </el-col>
        <el-col :span="8" class="step-group d-flex flex-column align-items-center">
          <div class="el-icon-odometer text-white mb-3"></div>
          <div class="w-100 mb-3 text-regular text-truncate">3 小时告警数</div>
          <div class="font-spiral">10</div>
        </el-col>
        <el-col :span="8" class="step-group d-flex flex-column align-items-center">
          <div class="el-icon-odometer text-white mb-3"></div>
          <div class="w-100 mb-3 text-regular text-truncate">24 小时告警数</div>
          <div class="font-spiral">115</div>
        </el-col>
      </el-row>
    </div>
    <div class="flex-grow-1 overflow-hidden pt-4 cursor-pointer" @mouseenter="swiperScrollStop" @mouseleave="swiperScrollAction">
      <swiper :options="swiperOption" ref="mySwiper">
        <swiper-slide class="p-2">
          <div class="text-overflow-line-2 mb-1">[测试系统]系统[BTPRODB]主机CPU使用率超过3.0% 且到
            目前为止已累计触发告警 2次。主机CPU使用率超过3主机CPU使用率超过3主机CPU使用率超过3主机CPU使用率超过3</div>
          <div class="text-regular">2019-05-23 18 : 25</div>
        </swiper-slide>
        <swiper-slide class="p-2">
          <div class="text-overflow-line-2 mb-1">[测试系统]系统[BTPRODB]主机CPU使用率超过3.0% 且到
            目前为止已累计触发告警 2次。</div>
          <div class="text-regular">2019-05-23 18 : 25</div>
        </swiper-slide>
        <swiper-slide class="p-2">
          <div class="text-overflow-line-2 mb-1">[测试系统]系统[BTPRODB]主机CPU使用率超过3.0% 且到
            目前为止已累计触发告警 2次。</div>
          <div class="text-regular">2019-05-23 18 : 25</div>
        </swiper-slide>
        <swiper-slide class="p-2">
          <div class="text-overflow-line-2 mb-1">[测试系统]系统[BTPRODB]主机CPU使用率超过3.0% 且到
            目前为止已累计触发告警 2次。</div>
          <div class="text-regular">2019-05-23 18 : 25</div>
        </swiper-slide>
        <swiper-slide class="p-2">
          <div class="text-overflow-line-2 mb-1">[测试系统]系统[BTPRODB]主机CPU使用率超过3.0% 且到
            目前为止已累计触发告警 2次。</div>
          <div class="text-regular">2019-05-23 18 : 25</div>
        </swiper-slide>

      </swiper>
    </div>
  </div>
</template>

<script>

  export default {
    name: 'DashboardLastMessage',
    data () {
      return {
        swiperOption: {
          direction: 'vertical',
          autoplay: {
            delay: 1000
          },
          loop: true,
          slidesPerView: '5',
          speed: 1500,
          height: 407
        }
      }
    },
    computed: {
      swiper () {
        return this.$refs.mySwiper.swiper
      }
    },
    methods: {
      swiperScrollStop: function () {
        this.swiper.autoplay.stop()
      },
      swiperScrollAction: function () {
        this.swiper.autoplay.start()
      }
    }
  }
</script>

<style scoped lang="scss">
  .step-group{
    & :first-child{
      width: 32px;
      height: 32px;
      border-radius: 50%;
      background-color: #67C13A;
      text-align: center;
      line-height: 32px;
      font-size: 24px;
    }
  }
  .step-line{
    border-color: #67C13A;
  }
  .translate-step-group{
    position: relative;
    top: -17px
  }
  .swiper-slide{
    box-sizing: border-box;
    &:nth-child(even){
      background-color: rgba(65, 75, 92, 0.3);
    }
  }
  .text-overflow-line-2{
    display: -webkit-box;
    overflow: hidden;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }
</style>
