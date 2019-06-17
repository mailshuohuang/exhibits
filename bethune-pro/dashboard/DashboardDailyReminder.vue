<template>
  <div class="dashboard-daily-reminder">
    <el-table
      :data="tableData"
      stripe
      class="w-100">
      <el-table-column
        prop="databaseName"
        label="数据库名">
      </el-table-column>
      <el-table-column
        label="巡检问题数"
        width="90"
        align="center">
        <template slot-scope="scope">
          <el-button type="text" class="font-spiral">{{ scope.row.databaseError }}</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
  export default {
    name: 'DashboardDailyReminder',
    data () {
      return {
        tableData: [
          {
            databaseName: 'Python 分析代码测试系统',
            databaseError: '6'
          },
          {
            databaseName: '测试Agent',
            databaseError: '2'
          },
          {
            databaseName: 'CBOSS',
            databaseError: '3'
          },
          {
            databaseName: '测试Agent',
            databaseError: '11'
          },
          {
            databaseName: '测试系统',
            databaseError: '5'
          },
          {
            databaseName: '12C',
            databaseError: '8'
          }
        ]
      }
    },
    created: function () {
    },
    methods: {}
  }
</script>

<style lang="scss">
  .dashboard-daily-reminder{
    .el-table{
      td{
        border-bottom: 0px;
        .cell{
          height: 45px;
          line-height: 45px;
        }
      }
    }
    .el-table::before{
      height: 0px;
    }
  }
</style>
