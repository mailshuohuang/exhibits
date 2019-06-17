<template>
  <div class="w-100 d-flex align-items-center flex-column hidden-progress-bar__outer">
    <el-row class="w-100 d-flex align-items-center flex-grow-1">
      <el-col :span="8" class="text-right pr-2 text-truncate">bethune-pub-develop</el-col>
      <el-col :span="16" class="pl-2">
        <div><span>平均会话数：<span class="text-white">18</span> 个</span><span>最大值：<span class="text-white">20</span> 个</span></div>
        <div><el-progress :percentage="100" :show-text="false"></el-progress></div>
      </el-col>
    </el-row>
    <el-row class="w-100 d-flex align-items-center flex-grow-1">
      <el-col :span="8" class="text-right pr-2 text-truncate">Python 分析代码测试系统</el-col>
      <el-col :span="16" class="pl-2">
        <div><span>平均会话数：<span class="text-white">10</span> 个</span><span>最大值：<span class="text-white">12</span> 个</span></div>
        <div><el-progress :percentage="80" :show-text="false"></el-progress></div>
      </el-col>
    </el-row>
    <el-row class="w-100 d-flex align-items-center flex-grow-1">
      <el-col :span="8" class="text-right pr-2 text-truncate">测试Agent</el-col>
      <el-col :span="16" class="pl-2">
        <div><span>平均会话数：<span class="text-white">10</span> 个</span><span>最大值：<span class="text-white">11</span> 个</span></div>
        <div><el-progress :percentage="60" :show-text="false"></el-progress></div>
      </el-col>
    </el-row>
    <el-row class="w-100 d-flex align-items-center flex-grow-1">
      <el-col :span="8" class="text-right pr-2 text-truncate">DG_测试</el-col>
      <el-col :span="16" class="pl-2">
        <div><span>平均会话数：<span class="text-white">5</span> 个</span><span>最大值：<span class="text-white">6</span> 个</span></div>
        <div><el-progress :percentage="40" :show-text="false"></el-progress></div>
      </el-col>
    </el-row>
    <el-row class="w-100 d-flex align-items-center flex-grow-1">
      <el-col :span="8" class="text-right pr-2 text-truncate">12C</el-col>
      <el-col :span="16" class="pl-2">
        <div><span>平均会话数：<span class="text-white">3</span> 个</span><span>最大值：<span class="text-white">5</span> 个</span></div>
        <div><el-progress :percentage="20" :show-text="false"></el-progress></div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: 'DashboardActiveSession',
    data () {
      return {}
    },
    methods: {}
  }
</script>

<style scoped lang="scss"></style>
