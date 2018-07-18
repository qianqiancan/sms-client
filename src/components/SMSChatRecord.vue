<template>
  <row>
    <div class="col-md-4">
      <el-table
        :data="tableData3"
        height="250"
        border
        style="width: 100%">
        <el-table-column
          prop="date"
          label="日期">
        </el-table-column>
        <el-table-column
          prop="name"
          label="姓名">
        </el-table-column>
        <el-table-column
          prop="address"
          label="地址">
        </el-table-column>
      </el-table>
    </div>
    <div class="col-md-8">
      <va-direct-chat
        theme="primary"
        :talkList="talkList"
        :contacts="contacts"
        title="短信来往"
        :badgeCount="30"
        placeholder=""
      ></va-direct-chat>
    </div>
  </row>
</template>

<script>
  import VADirectChat from '../widgets/VADirectChat.vue'
  export default {
      // name: 'sms-chat-record',
    data () {
      return {
        talkList: [
          {
            name: 'Alexander Pierce',
            date: new Date(),
            profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
            message: `Is this template really for free? That's unbelievable`,
            isMine: false
          },
          {
            name: 'Sarah Bullock',
            date: new Date(),
            profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
            message: `You better believe it!`,
            isMine: true
          }
        ],
        tableData3: [{
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-08',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-06',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-07',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }]
      }
    },
    components: {
      'va-direct-chat': VADirectChat
    }
  }
</script>

<style>

</style>
