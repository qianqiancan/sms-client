<template>
  <div>
    <row>
      <div class="col-md-12">
        <user-header></user-header>
      </div>
    </row>
    <!--<row>-->
      <!--<div class="col-md-4">-->
        <row>
          <div class="col-md-12 col-sm-12 col-xs-12">
            <div class="col-md-6">
              <el-button type="success" @click="CreateEdit = true">添加</el-button>
              <!--<el-button type="success" @click="EditGrouping">编辑</el-button>-->
            </div>
            <div class="text-right col-md-6">
              <el-button type="danger" @click="removeList" class="text-right">删除</el-button>
              <el-button type="danger" @click="messages = []" class="text-right">全部删除</el-button>
            </div>
          </div>
          <div class="col-md-12 col-sm-12 col-xs-12 ndy-border">
            <el-checkbox :indeterminate="isIndeterminate" v-model="checkAll" @change="handleCheckAllChange">全选</el-checkbox>
          </div>
        </row>
    <row>
      <div class="col-md-12">
        <el-collapse accordion>
          <el-collapse-item v-for="(item, index) in messages" style="padding-top: 20px;">
            <template slot="title">
              <div @click="btnUsershow(item)" v-model="neWshow" class="demo-color-box bg-success ndy-padding" :class="item.bgColor">
                <el-checkbox @change="handleCheckedCitiesChange(item)" v-model="item.neWshow"></el-checkbox>
                <span v-show='!item.delivery'>{{item.name}}</span>
                <el-button type="danger" @click="" class="pull-right" @click.stop style="margin-right: 8px; margin-top: 6px;" @click="item.content = []">全部删除</el-button>
                <el-button type="danger" @click="btnUser(item, index)" class="pull-right" @click.stop style="margin-right: 8px; margin-top: 6px;">删除用户</el-button>
                <el-button type="primary" @click="btnCreateUser(item, index)" class="pull-right" @click.stop style="margin-right: 0px; margin-top: 6px;">添加用户</el-button>
                <!--<el-form v-show='item.delivery' :model="item" :rules="rules" ref="create">-->
                  <!--<el-form-item label="" prop="name">-->
                    <!--<el-input v-model="item.name" auto-complete="off"></el-input>-->
                  <!--</el-form-item>-->
                <!--</el-form>-->
              </div>
            </template>
              <user-list v-if="item.content" :content="item.content" @new-content="newContent"></user-list>
          </el-collapse-item>
        </el-collapse>
      </div>
    </row>
    <el-dialog title="添加分组" :visible.sync="CreateEdit">
      <create-grouping @edit-content="deitContent"></create-grouping>
    </el-dialog>
    <!--<el-dialog title="编辑分组" :visible.sync="dialogFormVisible">-->
      <!--<edit-grouping :formVal="newmessages"></edit-grouping>-->
    <!--</el-dialog>-->
    <el-dialog title="新增用户" :visible.sync="CreateUser ">
      <!--@btn-cacel="btnCacel" @btn-deter="btnCacel"-->
      <grouping-user-create :userList="userListData" :defaultIndex="defaultIndex" @btn-user-data="btnUserData"></grouping-user-create>
    </el-dialog>
  </div>
</template>

<script>
  // 头部
  import UserHeader from './UserHeader.vue'
  // 编辑分组
  import EditGrouping from './EditGrouping.vue'
  // 添加分组
  import CreateGrouping from './CreateGrouping.vue'
  // 用户列表
  import UserList from './UserList.vue'
  // 分组添加用户
  import GroupingUserCreate from './GroupingUserCreate.vue'

  export default {
    components: {
      'user-header': UserHeader,
      'edit-grouping': EditGrouping,
      'create-grouping': CreateGrouping,
      'user-list': UserList,
      'grouping-user-create': GroupingUserCreate
    },
    data: function () {
      return {
        defaultIndex: [],    // 默认第几个元素选中
        CreateIndex: '',    // 当前点击分组的索引值
        messrMsg: false,    // 添加/删除用户状态
        CreateEdit: false,   // 添加分组
        CreateUser: false,  // 添加用户
        isIndeterminate: false,   // 全选的不确定状态
        checkAll: false,     // 全选状态
        show2: true,
        activeName: 1,
        // 初始化数据
        newmessages: [],
        // 初始化下标
        newIndex: [],
        // 获取数据
        userListData: [],
        // 当前分组下用户数据初始化
        GroupNewContent: [],
        messages: [
          {
            name: '组名1',
            neWshow: false,
            bgColor: 'bg-green',
            // 当前数据ID
            codeId: 101,
            delivery: false,
            content: [
              {
                id: 101,
                name: '王小虎1',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 201,
                name: '王小虎2',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 103,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 104,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 105,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'

              },
              {
                id: 106,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 107,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 108,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              }
            ]
          },
          {
            name: '组名2',
            neWshow: false,
            bgColor: 'bg-yellow',
            // 当前数据ID
            codeId: 102,
            delivery: false,
            content: [
              {
                id: 201,
                name: '王小虎2',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 202,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 203,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 204,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              }
            ]
          },
          {
            name: '组名3',
            neWshow: false,
            bgColor: 'bg-green',
            // 当前数据ID
            codeId: 103,
            delivery: false,
            content: [
              {
                id: 301,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 302,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 303,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 304,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              }
            ]
          },
          {
            name: '组名4',
            neWshow: false,
            bgColor: 'bg-yellow',
            // 当前数据ID
            codeId: 104,
            delivery: false,
            content: [
              {
                id: 401,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 402,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 403,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 404,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              }
            ]
          },
          {
            name: '组名5',
            neWshow: false,
            bgColor: 'bg-green',
            // 当前数据ID
            codeId: 105,
            delivery: false,
            content: [
              {
                id: 501,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 502,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 503,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              },
              {
                id: 504,
                name: '王小虎',
                date: this.nweDate(),
                address: '北京市朝阳区'
              }
            ]
          }
        ]
      }
    },
    methods: {
      // 点击分组事件
      btnUsershow (data) {
        // console.log(new Date())
      },
      // 时间处理
      nweDate () {
        var date = new Date()
        var month = date.getMonth() + 1 > 9 ? date.getMonth() + 1 : '0' + (date.getMonth() + 1)
        var rdata = date.getDate() > 9 ? date.getDate() : '0' + date.getDate()
        return date.getFullYear() + '-' + month + '-' + rdata
      },
      // 选中删除
      removeList () {
        var _this = this
        _this.newmessages.forEach((val, index) => {
          _this.messages.forEach((v, i) => {
            if (v.codeId === val.codeId) {
              _this.messages.splice(i, 1)
            }
          })
        })
      },
      // 全选
      handleCheckAllChange (val) {
        var _this = this
        this.isIndeterminate = !this.isIndeterminate
        this.messages.map((item, i) => {
          item.neWshow = val
        })
        _this.newmessages = []  // 初始化数据
        if (val === true) {
          _this.newmessages.push(_this.messages)
        } else {
          _this.newmessages = []
        }
      },
      // 单选
      handleCheckedCitiesChange (val) {
        // console.log('value==>', val)
        var _this = this
        if (val.neWshow === true) {
          _this.newmessages.push(val)
        } else {
          _this.newmessages.forEach((v, i) => {
            if (v.codeId === val.codeId) {
              _this.newmessages.splice(i, 1)
              _this.newIndex.splice(i, 1)
            }
          })
        }
        console.log('value==>', _this.newmessages, _this.newIndex)
        for (var i = 0; i < this.messages.length; i++) {
          if (this.messages[i].neWshow === false) {
            _this.isIndeterminate = true
            _this.checkAll = false
            break
          } else {
            _this.isIndeterminate = false
            _this.checkAll = true
          }
        }
      },
      // 添加分组
      deitContent (data) {
        console.log(data)
        this.CreateEdit = data.status
        if (data.content !== '') {
          this.messages.push(
            {
              name: data.content.name,
              neWshow: false,
              bgColor: data.content.bgColor,
              // 当前数据ID
              codeId: data.content.codeId,
              content: []
            }
          )
        }
      },
      // 获取用户数据
      _getUserData (data) {
        /**
         * @data      为当前点击分组的信息   需要参数可以在data => obj取值
         * @type {*[]}
         */
        var arrData = [
          {
            id: 101,
            name: '王小虎1',
            date: this.nweDate(),
            address: '北京市朝阳区'
          },
          {
            id: 201,
            name: '王小虎2',
            date: this.nweDate(),
            address: '北京市朝阳区'
          },
          {
            id: 301,
            name: '王小虎3',
            date: this.nweDate(),
            address: '北京市朝阳区'
          },
          {
            id: 401,
            name: '王小虎4',
            date: this.nweDate(),
            address: '北京市朝阳区'
          },
          {
            id: 501,
            name: '王小虎5',
            date: this.nweDate(),
            address: '北京市朝阳区'

          },
          {
            id: 601,
            name: '王小虎6',
            date: this.nweDate(),
            address: '北京市朝阳区'
          },
          {
            id: 701,
            name: '王小虎7',
            date: this.nweDate(),
            address: '北京市朝阳区'
          },
          {
            id: 801,
            name: '王小虎8',
            date: this.nweDate(),
            address: '北京市朝阳区'
          }
        ]
        this.userListData = arrData
      },
      // 添加用户
      btnCreateUser (data, index) {
        var _this = this
        this.CreateUser = true      // 展示弹窗显示列表
        this._getUserData(data)     // 调取请求数据的方法
        this.CreateIndex = index    // 记录当前点击分组的索引值
        // console.log(this.CreateIndex)
        data.content.forEach((val, index) => {
          _this.userListData.forEach((v, i) => {
            if (v.id === val.id) {
              _this.defaultIndex.push(i)
            }
          })
        })
      },
      // 确认添加用户
      btnUserData (data) {
        console.log(data)
        var _this = this
        this.CreateUser = data.msg      // 隐藏弹窗显示列表
        if (data.userObj.length !== 0) {
          data.userObj.forEach((val, index) => {
            _this.messages[_this.CreateIndex].content.push(val)
          })
        }
      },
      // 当前分组下选中的用户
      newContent (data) {
        this.GroupNewContent = data
      },
      // 删除用户
      btnUser (data, index) {
        var _this = this
        this.GroupNewContent.forEach((val, u) => {
          _this.messages[index].content.forEach((v, i) => {
            if (val.id === v.id) {
              _this.messages[index].content.splice(i, 1)
            }
          })
        })
      }
      // EditGrouping () {
      //   var _this = this
      //   _this.newmessages.forEach((val, index) => {
      //     _this.messages.forEach((v, i) => {
      //       if (v.codeId === val.codeId) {
      //         v.delivery = true
      //         console.log(v.delivery)
      //       }
      //     })
      //   })
      // }
    }
  }
</script>

<style scoped>

  .content-wrapper {
    background: #fff;
  }
  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .clearfix:before,
  .clearfix:after {
    display: table;
    content: "";
  }
  .clearfix:after {
    clear: both
  }

  .box-card {
    width: 480px;
  }
  .ndy-border {
    border-top: 1px solid #ddd;
    margin-top: 20px;
    box-sizing: border-box;
    padding: 5px 10px 5px 25px;
  }
  .ndy-padding {
    box-sizing: border-box;
    padding-left: 10px;
    padding-right: 10px;
    border-radius: 5px;
  }
</style>
