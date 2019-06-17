<template>
  <el-container direction="vertical">
    <div>控制台</div>
    <el-row class="my-2">
      <el-col :span="18" class="pr-2">
        <el-row class="pb-2">
          <el-col :span="6" class="pr-2">
            <div class="widget px-3">
              <div class="widget-header d-flex align-items-center justify-content-between">
                <span class="text-white">
                   数据库概览
                  <el-tooltip>
                      <div slot="content">
                      <p class="my-1">展示纳入 Bethune  监控的数据库各个版本的数量，分为单实例和RAC，一天刷新一次</p>
                    </div>
                    <span class="el-icon-warning text-regular"></span>
                  </el-tooltip>
                </span>
                <div>
                  总计 <span>-</span> 套
                </div>
              </div>
              <div class="py-2 d-flex align-items-stretch" style="height: 250px;">
                <dashboard-database-overview></dashboard-database-overview>
              </div>
            </div>
          </el-col>
          <el-col :span="9" class="px-2">
            <div class="widget px-3">
              <div class="widget-header d-flex align-items-center">
                <span class="text-white">
                  容量概览
                  <el-tooltip>
                    <div slot="content">
                      <p class="my-1">展示纳入 Bethune  监控的所有数据库数据文件总容量，以及剩余容量，10分钟刷新一次</p>
                    </div>
                    <span class="el-icon-warning text-regular"></span>
                  </el-tooltip>
                </span>
              </div>
              <div class="py-2 d-flex align-items-stretch" style="height: 250px;">
                <dashboard-space-overview></dashboard-space-overview>
              </div>
            </div>
          </el-col>
          <el-col :span="9" class="pl-2">
            <div class="widget px-3">
              <div class="widget-header d-flex align-items-center">
                <span class="text-white">
                  近1小时活动会话TOP5
                  <el-tooltip>
                      <div slot="content">
                      <p class="my-1">展示纳入 Bethune  监控的所有数据库最近1小时活动会话数量。包括紧一小时的平均值和最大值。1分钟刷新一次</p>
                    </div>
                    <span class="el-icon-warning text-regular"></span>
                  </el-tooltip>
                </span>
              </div>
              <div class="py-2 d-flex align-items-stretch" style="height: 250px;">
                <dashboard-active-session></dashboard-active-session>
              </div>
            </div>
          </el-col>
        </el-row>
        <div class="w-100">
          <dashboard-database-warning-overview></dashboard-database-warning-overview>
        </div>
      </el-col>
      <el-col :span="6" class="pl-2">
        <div class="widget px-3 mb-3">
          <div class="widget-header d-flex align-items-center">
            <span class="text-white">
              最近告警
              <el-tooltip>
                <div slot="content">
                  <p class="my-1">展示纳入 Bethune  监控的所有数据库最近告警数量，以及最近半天的告警详情滚动消息</p>
                </div>
                <span class="el-icon-warning text-regular"></span>
              </el-tooltip>
            </span>
          </div>
          <div class="py-2 d-flex align-items-stretch" style="height: 550px">
            <dashboard-last-message></dashboard-last-message>
          </div>
        </div>
        <div class="widget px-3 mb-3">
          <div class="widget-header d-flex align-items-center">
            <span class="text-white">
              每日提醒
              <el-tooltip>
                <div slot="content">
                  <p class="my-1">展示Bethune 昨日自动巡检发现的问题。白求恩内置的每日自动巡检算法将检查数据库应用变化带来的潜在风险。</p>
                </div>
                <span class="el-icon-warning text-regular"></span>
              </el-tooltip>
            </span>
          </div>
          <div>
            <dashboard-daily-reminder></dashboard-daily-reminder>
            <app-common-loading v-if="false" :height="460"></app-common-loading>
          </div>
        </div>
      </el-col>
    </el-row>
  </el-container>
</template>

<script>
  import DashboardDatabaseOverview from './DashboardDatabaseOverview'
  import DashboardSpaceOverview from './DashboardSpaceOverview'
  import DashboardActiveSession from './DashboardActiveSession'
  import DashboardLastMessage from './DashboardLastMessage'
  import DashboardDailyReminder from './DashboardDailyReminder'
  import DashboardDatabaseWarningOverview from './DashboardDatabaseWarningOverview'

  export default {
    name: 'Dashboard',
    components: {
      DashboardDatabaseOverview,
      DashboardSpaceOverview,
      DashboardActiveSession,
      DashboardLastMessage,
      DashboardDailyReminder,
      DashboardDatabaseWarningOverview
    },
    data () {
      return {
        databaseOverview: {},
        spaceOverview: {},
        activeSession: [],
        lastMessage: {},
        dailyReminder: {},
        databaseList: []
      }
    },
    methods: {}
  }
</script>

<style scoped lang="scss">

</style>
