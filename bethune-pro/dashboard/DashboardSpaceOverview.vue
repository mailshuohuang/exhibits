<template>
  <el-row class="w-100 d-flex align-items-stretch">
    <el-col :span="11" class="pr-1 position-relative">
      <div class="pie-title text-center">
        <div class="pb-1">已使用 <span class="font-spiral text-white">{{chartData.used}}</span><span>GB</span></div>
        <div class="pt-1 database-space-border">
          <span>总容量</span>
          <span  class="text-white">
            {{chartData.total}}
          </span>
        </div>
      </div>
      <v-chart style="height: 250px" :options="chartData.option" :autoresize="true"/>
    </el-col>
    <el-col :span="13" class="pl-1 d-flex flex-column">
      <div class="my-2 text-white">近 1h 容量增加最快Top3系统：</div>
      <div class="flex-grow-1 d-flex flex-column align-items-center">
        <el-row class="w-100 flex-grow-1 d-flex align-items-center">
          <el-col :span="16" class="text-right pr-2 text-truncate">
            <el-tooltip placement="top-start" :content="'bethune-pub-develop'"><span>bethune-pub-develop</span>
            </el-tooltip>
          </el-col>
          <el-col :span="8" class="pl-2"><span class="font-spiral pr-1 text-white">8.4</span><span
            class="text-white pl-1">MB</span></el-col>
        </el-row>
        <el-row class="w-100 flex-grow-1 d-flex align-items-center">
          <el-col :span="16" class="text-right pr-2 text-truncate">
            <el-tooltip placement="top-start" :content="'测试系统'"><span>测试系统</span>
            </el-tooltip>
          </el-col>
          <el-col :span="8" class="pl-2"><span class="font-spiral pr-1 text-white">4.7</span><span
            class="text-white pl-1">MB</span></el-col>
        </el-row>
        <el-row class="w-100 flex-grow-1 d-flex align-items-center">
          <el-col :span="16" class="text-right pr-2 text-truncate">
            <el-tooltip placement="top-start" :content="'DG_测试'"><span>DG_测试</span>
            </el-tooltip>
          </el-col>
          <el-col :span="8" class="pl-2"><span class="font-spiral pr-1 text-white">9.8</span><span
            class="text-white pl-1">MB</span></el-col>
        </el-row>
      </div>
    </el-col>
  </el-row>
</template>

<script>
  export default {
    name: 'DashboardSpaceOverview',
    data () {
      return {
        chartData: {
          used: '747.3',
          total: '844.4 GB',
          option: {
            color: ['#4a6879'],
            legend: { 'show': false },
            series: [
              {
                name: 'Line 1',
                type: 'pie',
                radius: ['75%', '90%'],
                itemStyle: {
                  normal: {
                    label: {
                      show: false
                    },
                    labelLine: {
                      show: false
                    }
                  }
                },
                hoverAnimation: false,
                data: [
                  {
                    value: 802503655424,
                    name: '01',
                    itemStyle: {
                      normal: {
                        color: {
                          colorStops: [
                            {
                              offset: 0,
                              color: 'rgb(20, 214, 237)'
                            },
                            {
                              offset: 1,
                              color: 'rgb(31, 163, 255)'
                            }
                          ]
                        },
                        label: {
                          show: false
                        },
                        labelLine: {
                          show: false
                        }
                      }
                    }
                  },
                  {
                    name: '02',
                    value: 104249819136
                  }
                ]
              }
            ]
          }
        }
      }
    },
    methods: {}
  }
</script>

<style scoped lang="scss">
  .pie-title{
    width: 120px;
    height: 60px;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    margin: auto;
  }
  .database-space-border{
    border-top: 1px solid #44536a;
  }
</style>
