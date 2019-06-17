<template>
  <div class="databaseOverview w-100 d-flex flex-column text-white">
    <el-row class="d-flex align-items-center flex-grow-1">
      <el-col :span="14" class="pr-1">
        <img style="width: 100px" src="../../assets/images/oracle-10g.png">
      </el-col>
      <el-col :span="10" class="pl-1">
        <div class="d-flex justify-content-between">
          <div class="text-center w-50">
            <div class="mb-1 font-spiral">1</div>
            <div class="text-regular text-truncate w-100">单实例</div>
          </div>
          <div class="text-center w-50">
            <div class="mb-1 font-spiral">1</div>
            <div class="text-regular text-truncate w-100" style="font-family: initial;">RAC</div>
          </div>
        </div>
      </el-col>
    </el-row>
    <el-row class="d-flex align-items-center flex-grow-1">
      <el-col :span="14" class="pr-1">
        <img style="width: 100px" src="../../assets/images/oracle-11g.png">
      </el-col>
      <el-col :span="10" class="pl-1">
        <div class="d-flex justify-content-between">
          <div class="text-center w-50">
            <div class="mb-1 font-spiral">5</div>
            <div class="text-regular text-truncate w-100">单实例</div>
          </div>
          <div class="text-center w-50">
            <div class="mb-1 font-spiral">2</div>
            <div class="text-regular text-truncate w-100" style="font-family: initial;">RAC</div>
          </div>
        </div>
      </el-col>
    </el-row>
    <el-row class="d-flex align-items-center flex-grow-1">
      <el-col :span="14" class="pr-1">
        <img style="width: 100px" src="../../assets/images/oracle-12c.png">
      </el-col>
      <el-col :span="10" class="pl-1">
        <div class="d-flex justify-content-between">
          <div class="text-center w-50">
            <div class="mb-1 font-spiral">4</div>
            <div class="text-regular text-truncate w-100">单实例</div>
          </div>
          <div class="text-center w-50">
            <div class="mb-1 font-spiral">9</div>
            <div class="text-regular text-truncate w-100" style="font-family: initial;">RAC</div>
          </div>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  export default {
    name: 'DashboardDatabaseOverview',
    data () {
      return {}
    },
    methods: {}
  }
</script>

<style scoped lang="scss">
  .databaseOverview > *:not(:last-child){
    border-bottom: 1px dashed rgb(68, 83, 106);
  }
</style>
