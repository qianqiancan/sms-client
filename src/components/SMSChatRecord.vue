<template>
  <row>
    <div class="col-md-6">
      <el-table
        :data="tableData3"
        height="600"
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
        <el-table-column
          fixed="right"
          label="操作"
          width="100">
          <template slot-scope="scope">
            <el-button @click="handleClick(scope.row)" type="success">查看</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
    <div class="col-md-6">
      <va-direct-chat
        theme="primary"
        :talkList="talkList"
        :contacts="contacts"
        title="短信来往"
        :badgeCount="100"
        @send-chat-content="btnSendChat"
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
            date: this.TimeDate(),
            profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
            message: `Is this template really for free? That's unbelievable`,
            isMine: false
          },
          {
            name: 'Sarah Bullock',
            date: this.TimeDate(),
            profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
            message: `You better believe it!`,
            isMine: true
          }
        ],
        tableData3: [{
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: '王小虎',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: '王小虎',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            }
          ]
        }, {
          date: '2016-05-02',
          name: '张文才',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: '张文才',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: '张文才',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            }
          ]
        }, {
          date: '2016-05-04',
          name: '流光年',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: '流光年',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: '流光年',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            }
          ]
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: '王小虎',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: '王小虎',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            }
          ]
        }, {
          date: '2016-05-08',
          name: '王运用',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: '王运用',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: '王运用',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            }
          ]
        }, {
          date: '2016-05-06',
          name: '王小虎123',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: '王小虎123',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: '王小虎123',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            }
          ]
        }, {
          date: '2016-05-07',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          chatRecord: [
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: 'admin',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `Is this template really for free? That's unbelievable`,
              isMine: false
            },
            {
              name: '王小虎',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            },
            {
              name: '王小虎',
              date: this.TimeDate(),
              profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
              message: `You better believe it!`,
              isMine: true
            }
          ]
        }]
      }
    },
    methods: {
      btnSendChat (str) {
        var _this = this
        console.log('str==>', str)
        this.talkList.push({
          name: 'admin',
          date: _this.TimeDate(),
          profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
          message: str,
          isMine: false
        })
      },
      handleClick (data) {
        this.talkList = data.chatRecord
      },
      TimeDate () {
        var date = new Date()
        var month = date.getMonth() + 1 > 9 ? date.getMonth() + 1 : '0' + (date.getMonth() + 1)
        var rdata = date.getDate() > 9 ? date.getDate() : '0' + date.getDate()
        return date.getFullYear() + '-' + month + '-' + rdata
      }
    },
    components: {
      'va-direct-chat': VADirectChat
    }
  }
</script>

<style>

</style>
