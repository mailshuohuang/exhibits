<template>
  <el-dialog
    class="white-bg"
    title="编辑数据库"
    :visible.sync="dialogVisible"
    width="533px"
    @close="handleCloseDialog">
    <div class="mb-3 text-dark font-weight-bold">
      已选数据库：
    </div>
    <div>
      <el-tag
        class="mr-3 mb-2"
        v-for="tag in tagList"
        :key="tag.databaseId"
        closable
        :disable-transitions="false"
        type="info"
        @close="handleCloseTag(tag)">
        {{tag.databaseName}}
      </el-tag>
    </div>
    <div class="search-checked-group-widget">
      <div class="search-checked-group-widget__header px-2 d-flex align-items-center justify-content-between">
        <el-input placeholder="搜索数据库" v-model="databaseSearchKey" class="border-none w-50"></el-input>
        <el-button type="text" class="el-icon-close" @click="clearDatabaseSearchKey"></el-button>
      </div>
      <div class="search-checked-group-widget__body">
        <el-checkbox-group
          v-model="checkedDatabase"
          :max="12">
          <el-checkbox class="w-50 m-0 pl-3 my-2 box-sizing-border-box" v-for="item in databaseList" :label="item" :key="item.databaseId">{{item.databaseName}}</el-checkbox>
        </el-checkbox-group>
      </div>
    </div>
    <div class="text-black-50">最多可以选择12个数据库</div>
    <div class="d-flex align-items-center justify-content-between">
      <div></div>
      <div>
        <el-button class="mr-3">取消</el-button>
        <el-button type="success">保存</el-button>
      </div>
    </div>
  </el-dialog>
</template>

<script>
  export default {
    name: 'DashboardEditDatabaseDialog',
    data () {
      return {
        dataList: [
          {
            databaseName: 'DG测试',
            databaseId: 0
          },
          {
            databaseName: '测试系统',
            databaseId: 1
          },
          {
            databaseName: 'develop',
            databaseId: 3
          },
          {
            databaseName: '111112C',
            databaseId: 4
          },
          {
            databaseName: '21112C',
            databaseId: 5
          },
          {
            databaseName: '22212C',
            databaseId: 6
          },
          {
            databaseName: '23112C',
            databaseId: 7
          },
          {
            databaseName: '12C',
            databaseId: 2
          },
          {
            databaseName: '212C',
            databaseId: 8
          }
        ],
        checkedDatabase: [],
        databaseSearchKey: '',
        dialogVisible: true,
        tags: [
          {
            name: 'bethune-pub-develop',
            id: 0
          },
          {
            name: '测试Agent',
            id: 1
          },
          {
            name: 'DG测试',
            id: 2
          },
          {
            name: '12C',
            id: 3
          },
          {
            name: 'bethune-pub',
            id: 4
          },
          {
            name: 'develop',
            id: 5
          }
        ]
      }
    },
    methods: {
      handleCloseDialog: function () {
        this.$emit('handleClose')
      },
      handleCloseTag: function (tag) {
        this.checkedDatabase.splice(this.checkedDatabase.findIndex(item => item.databaseId === tag.databaseId), 1)
      },
      clearDatabaseSearchKey: function () {
        this.databaseSearchKey = ''
      }
    },
    computed: {
      tagList: function () {
        const tags = []
        this.dataList.forEach(item => {
          this.checkedDatabase.forEach(database => {
            if (database === item) {
              tags.push(item)
            }
          })
        })
        return tags
      },
      databaseList: function () {
        if (this.databaseSearchKey) {
          return this.dataList.filter(item => {
            return item.databaseName.indexOf(this.databaseSearchKey) > -1
          }).sort((a, b) => {
            return a.databaseName.indexOf(this.databaseSearchKey) - b.databaseName.indexOf(this.databaseSearchKey)
          })
        } else {
          return this.dataList
        }
      }
    },
    created: function () {
      this.checkedDatabase = [this.databaseList[0], this.databaseList[1]]
    }
  }
</script>

<style scoped lang="scss">
  .box-sizing-border-box{
    box-sizing: border-box;
  }
  .search-checked-group-widget{
    border: 1px solid #B0B9C0;
    height: 320px;
    border-radius:4px;
    &__header{
      height: 40px;
      border-bottom: 1px solid #B0B9C0;
    }
  }
</style>
