<template>
  <div>
    <div class="d-flex align-items-center justify-content-between" style="height: 50px;">
      <ul class="d-flex align-items-center m-0 p-0">
        <li>
          <span :class="{'text-white': activeType === 'all'}" @click="handleInstanceGroup('all')">所有</span>
        </li>
        <li class="mx-3">|</li>
        <li>
          <span :class="{'text-white': activeType === 'collection'}" @click="handleInstanceGroup('collection')">收藏</span>
        </li>
        <li class="mx-3">|</li>
        <li>
          <span :class="{'text-white': activeType === 'lastHourWarningNum'}" @click="handleInstanceGroup('lastHourWarningNum')">近1小时告警数最多</span>
        </li>
      </ul>
      <el-button type="success" @click="editDatabase">编辑数据库</el-button>
    </div>
    <div v-if="databaseList.length > 0">
      <transition-group
        class="w-100 d-flex flex-wrap"
        name="cell"
        tag="div">
        <div class="cell mb-3" v-for="item of databaseList" :key="item.databaseId">
          <div class="widget px-3">
            <div class="widget-header d-flex align-items-center justify-content-between">
              <span class="text-white">{{ item.databaseName }}</span>
              <el-button-group v-if="item.databaseType === '12C'">
                <el-button
                  :type="item.databaseSpaceType === 'instance' ? 'success' : ''"
                  :plain="item.databaseSpaceType !== 'instance'"
                  @click="handleDatabaseSpaceType(item, 'instance')">实例视角</el-button>
                <el-button
                  :type="item.databaseSpaceType === 'container' ? 'success' : ''"
                  :plain="item.databaseSpaceType !== 'container'"
                  @click="handleDatabaseSpaceType(item, 'container')">容器视角</el-button>
              </el-button-group>
              <span @click="handleCollection(item)">
                <span class="el-icon-star-on star-light" v-if="item.collection"><span class="text-white ml-2">收藏</span></span>
                <span class="el-icon-star-off" v-if="!item.collection"><span class="ml-2">收藏</span></span>

              </span>
            </div>
            <div class="py-2" style="height: 305px;">
              <app-common-no-data v-if="true" :height="250"></app-common-no-data>
              <!--<v-chart :options="option" :autoresize="true"></v-chart>-->
            </div>
          </div>
        </div>
      </transition-group>
    </div>
    <div v-if="databaseList.length === 0">
      <div class="cell mb-3">
        <div class="widget px-3 d-flex justify-content-center align-items-center" style="height: 370px;">
          <div class="text-center" @click="editDatabase">
            <el-button type="text" class="add-database el-icon-plus" style=""></el-button>
            <div class="mt-3">添加数据库</div>
          </div>
        </div>
      </div>
    </div>
    <dashboard-edit-database-dialog v-if="dialogVisible" @handle-close="handleClose"></dashboard-edit-database-dialog>
  </div>
</template>

<script>
  import DashboardEditDatabaseDialog from './DashboardEditDatabaseDialog'
  export default {
    name: 'DashboardDatabaseWarningOverview',
    components: {
      DashboardEditDatabaseDialog
    },
    data () {
      return {
        activeType: 'all',
        dialogVisible: false,
        params: [
          {
            databaseName: '12C',
            databaseId: 1,
            databaseSpaceType: 'instance',
            databaseType: '12C',
            collection: true,
            lastHourWarningNum: 5,
            systemScore: '66',
            instanceList: []
          },
          {
            databaseName: 'bethune-pub-develop',
            databaseId: 2,
            databaseSpaceType: 'instance',
            databaseType: 'bethune-pub-develop',
            collection: false,
            lastHourWarningNum: 5,
            systemScore: '66',
            instanceList: []
          },
          {
            databaseName: 'DG测试',
            databaseId: 3,
            databaseSpaceType: 'instance',
            databaseType: 'DG测试',
            collection: false,
            lastHourWarningNum: 5,
            systemScore: '66',
            instanceList: []
          },
          {
            databaseName: '测试Agent',
            databaseId: 4,
            databaseSpaceType: 'instance',
            databaseType: '测试Agent',
            collection: true,
            lastHourWarningNum: 5,
            systemScore: '66',
            instanceList: []
          },
          {
            databaseName: 'develop',
            databaseId: 5,
            databaseSpaceType: 'instance',
            databaseType: 'DG测试',
            collection: false,
            lastHourWarningNum: 5,
            systemScore: '66',
            instanceList: []
          },
          {
            databaseName: 'DG测试',
            databaseId: 6,
            databaseSpaceType: 'instance',
            databaseType: 'DG测试',
            collection: true,
            lastHourWarningNum: 5,
            systemScore: '66',
            instanceList: []
          }
        ]
      }
    },
    methods: {
      handleCollection: function (item) {
        item.collection = !item.collection
      },
      editDatabase: function () {
        this.dialogVisible = true
      },
      handleInstanceGroup: function (type) {
        this.activeType = type
      },
      handleDatabaseSpaceType: function (item, type) {
        item.databaseSpaceType = type
      },
      handleClose: function () {
        this.dialogVisible = false
      }
    },
    created: function () {
      this.params.forEach((item, index) => {
        item.id = index
      })
    },
    computed: {
      databaseList: function () {
        if (this.activeType === 'all') {
          return this.params
        } else if (this.activeType === 'collection') {
          return this.params.filter(item => item.collection)
        } else if (this.activeType === 'lastHourWarningNum') {
          return this.params.map(item => item).sort((a, b) => {
            return b.collection - a.collection
          })
        } else {
          return []
        }
      }
    }
  }
</script>

<style scoped lang="scss">
  .star-light {
    color: #EEAB25;
    font-size: 14px;
  }

  ul,li{
    list-style: none;
  }

  .cell {
    width: 33.3%;
    box-sizing: border-box;
    &:nth-child(3n) {
      padding-left: 8px;
    }
    &:nth-child(3n+1) {
      padding-right: 8px;
    }
    &:nth-child(3n+2) {
      padding: 0 8px;
    }
  }

  .cell-move {
    transition: transform 1s;
  }

  .cell-enter, .cell-leave-to {
    opacity: 0;
    height: 0;
    transform: translateY(-30px) scale(0);
  }

  .cell-enter-active, .cell-leave-active {
    transition: all 1s;
  }
  .cell-leave-active{
    transition: all 0.5s;
  }
  .add-database{
    width: 70px;
    height: 70px;
    font-size: 30px;
    border: 1px dashed #627797;
    background-color: rgba(255, 255, 255, 0.1);
  }
</style>
