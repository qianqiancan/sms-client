<template>
  <div>
    <row>
      <div class="col-md-12">
        <user-header></user-header>
      </div>
    </row>
    <row>
      <div class="col-md-4 demo-color-box bg-warning">
        <el-tree
          :data="data2"
          node-key="id"
          show-checkbox
          :default-expanded-keys="[1, 1, 1]"
          :default-checked-keys="[5]"
          :props="defaultProps"
          class="demo-color-box bg-warning"
          @node-click="btnGrouping">
        </el-tree>
      </div>
      <div class="col-md-8">
        <el-input
        type="textarea"
        :rows="10"
        title="请输入短信内容："
        placeholder="选择用户输入您想要发送的内容，点击发送"
        rowCount="20" v-model="sendMastion.content">
        </el-input>
        <el-row type="flex" justify="right" class="text-center" style="margin-top: 10px; margin-bottom: 10px">
          <div class="col-md-12">
            <el-button type="primary" label="right" @click="btnSend" plain style="width: 100%">发送</el-button>
          </div>
        </el-row>
      </div>
    </row>
    <row>
      <div class="col-md-12">
        <user-display :userData="userData" :userMsg="userMsg" @btn-select="btnSelect"></user-display>
      </div>
    </row>
  </div>
</template>

<script>
  // 头部
  import UserHeader from './UserHeader.vue'
  import VATextareaGroup from '../components/VATextareaGroup'
  import UserDisplay from './UserDisplay.vue'
  export default {
    components: {
      'user-header': UserHeader,
      'va-textarea-group': VATextareaGroup,
      'user-display': UserDisplay
    },
    data () {
      return {
        data2: [{
          id: 1,
          label: '一级分组 1',
          treeUserData: [{
            id: 101,
            grouping: '一级分组 1',
            name: '王小虎1',
            phone: '138989898989'
          }, {
            id: 102,
            grouping: '一级分组 1',
            name: '王小虎1',
            phone: '13111113534111'
          }, {
            id: 103,
            grouping: '一级分组 1',
            name: '王小虎1',
            phone: '131123432411111'
          }, {
            id: 104,
            grouping: '一级分组 1',
            name: '王小虎1',
            phone: '1311679867911111'
          }, {
            id: 105,
            grouping: '一级分组 1',
            name: '王小虎1',
            phone: '1311000011111'
          }, {
            id: 106,
            grouping: '一级分组 1',
            name: '王小虎1',
            phone: '131111111111'
          }],
          children: [{
            id: 4,
            label: '二级 1-1',
            children: [{
              id: 9,
              label: '三级 1-1-1'
            }, {
              id: 10,
              label: '三级 1-1-2'
            }]
          }]
        }, {
          id: 2,
          label: '一级分组 2',
          treeUserData: [{
            id: 201,
            grouping: '一级分组 2-1',
            name: '王小虎2',
            phone: '132222222222'
          }, {
            id: 202,
            grouping: '一级分组 2-2',
            name: '王小虎2',
            phone: '132222222222'
          }, {
            id: 203,
            grouping: '一级分组 2-3',
            name: '王小虎2',
            phone: '132222222222'
          }, {
            id: 204,
            grouping: '一级分组 2-4',
            name: '王小虎2',
            phone: '132222222222'
          }],
          children: [{
            id: 5,
            label: '二级 2-1'
          }, {
            id: 6,
            label: '二级 2-2'
          }]
        }, {
          id: 3,
          label: '一级分组 3',
          treeUserData: [{
            id: 301,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 302,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 303,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 304,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 305,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 306,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 307,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 308,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 309,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }, {
            id: 310,
            grouping: '一级分组 3',
            name: '王小虎3',
            phone: '133333333333'
          }]
          // children: [{
          //   id: 7,
          //   label: '二级 3-1'
          // }, {
          //   id: 8,
          //   label: '二级 3-2'
          // }]
        }],
        // 用户列表的展示状态
        userMsg: true,
        // 需要展示当前分组的下的用户数据
        userData: [],
        // 需要发送的数据源
        sendMastion: {
          id: '666',
          name: 'admin',
          phones: [],
          content: '',
          date: new Date(),
          groupings: [],
          userIndex: []
        },
        sendArrPhone: [],
        sendArrGroupings: [],
        defaultProps: {
          children: 'children',
          label: 'label'
        }
      }
    },
    methods: {
      btnGrouping (data) {
        // alert('出发了选项卡')
        this.userData = data.treeUserData
        this.userMsg = true
      },
      btnSelect (obj) {
        console.log('obj||||》', obj)
        this.sendMastion.phones = obj.arrPhone
        this.sendMastion.groupings = obj.arrGroupings
      },
      // 向后端发送数据请求
      btnSend () {
        console.log(this.sendMastion)
      }
    }
  }
</script>

<style scoped>

</style>
