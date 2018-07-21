<template>
  <section class="content">
    <row>

      <div class="col-md-12 col-sm-12 col-xs-12" slot-scope='scope'>
        <el-button @click=" dialogFormVisible = true " plain>新增</el-button>
        <el-button type="primary" plain>导入</el-button>
        <el-button type="primary" @click="btnFormVisible" plain>{{saveName}}</el-button>
        <el-button type="success" @click="removeData" plain>删除</el-button>
        <el-button type="danger" @click=" tableData = [] " plain>全部删除</el-button>
      </div>
    </row>
    <row>
      <div class="col-md-12 col-sm-12 col-xs-12">
          <el-table
            @selection-change="changeFun"
            :data="tableData"
            style="width: 100%">
            <el-table-column
              type="selection"
              width="55">
            </el-table-column>
            <el-table-column
              prop="date"
              label="日期"
              width="240">
              <template slot-scope='scope'>
                <span v-show='!scope.row.delivery'>{{scope.row.date1}}</span>
                <el-form v-show='scope.row.delivery' :model="scope.row" :rules="rules" ref="create">
                  <el-form-item label="" prop="date2">
                    <el-date-picker type="date" placeholder="选择日期" v-model="scope.row.date2" suffix-icon='el-icon-edit'></el-date-picker>
                  </el-form-item>
                </el-form>
                <!--<el-date-picker type='date' v-show='scope.row.delivery' v-model='scope.row.date' placeholder='请输入内容' suffix-icon='el-icon-edit' prop="date2"></el-date-picker>-->
                <!--<el-date-picker-->
                <!--v-show='scope.row.delivery'-->
                <!--v-model='scope.row.date'-->
                <!--type='date'-->
                <!--placeholder=''-->
                <!--&gt;</el-date-picker>-->
              </template>
            </el-table-column>
            <el-table-column
              prop="name"
              label="姓名"
              width="180">
              <template slot-scope='scope'>
                <span v-show='!scope.row.delivery'>{{scope.row.name}}</span>
                <el-form v-show='scope.row.delivery' :model="scope.row" :rules="rules" ref="create">
                  <el-form-item label="" prop="name">
                    <el-input v-model="scope.row.name" auto-complete="off"></el-input>
                  </el-form-item>
                </el-form>
                <!--<el-input type='text' v-show='scope.row.delivery' v-model='scope.row.name' placeholder='请输入内容' suffix-icon='el-icon-edit'></el-input>-->
              </template>
            </el-table-column>
            <el-table-column
              prop="phone"
              label="电话">
              <template slot-scope='scope'>
                <span v-show='!scope.row.delivery'>{{scope.row.phone}}</span>
                <el-form v-show='scope.row.delivery' :model="scope.row" :rules="rules" ref="create">
                  <el-form-item label="" prop="phone">
                    <el-input v-model="scope.row.phone"></el-input>
                  </el-form-item>
                </el-form>
                <!--<el-input type='text' v-show='scope.row.delivery' v-model='scope.row.phone' placeholder='请输入内容' suffix-icon='el-icon-edit'></el-input>-->
              </template>
            </el-table-column>
          </el-table>
      </div>
    </row>
    <el-dialog title="新增用户" :visible.sync=" dialogFormVisible ">
      <user-edit @btn-cacel="btnCacel" @btn-deter="btnCacel"></user-edit>
    </el-dialog>
  </section>

</template>

<script>
  import UserEdit from './UserEdit.vue'
  export default {
    data: function () {
      return {
        dialogFormVisible: false,
        saveName: '编辑',
        saveMsg: true,
        tableData: [{
          id: 1,
          date1: '2016-05-02',
          date2: '2016-05-02',
          name: '王小虎',
          phone: '13333333333',
          delivery: false
        }, {
          id: 2,
          date1: '2016-05-04',
          date2: '2016-05-04',
          name: '王小虎',
          phone: '13222222222',
          delivery: false
        }, {
          id: 3,
          date1: '2016-05-01',
          date2: '2016-05-01',
          name: '王小虎',
          phone: '13111111111',
          delivery: false
        }, {
          id: 4,
          date1: '2016-05-03',
          date2: '2016-05-03',
          name: '王小虎',
          phone: '13444444444',
          delivery: false
        }],
        // 表单验证
        rules: {
          date2: [
            {type: 'date', required: true, message: '请选择日期', trigger: 'change'}
          ],
          name: [
            {required: true, message: '请输入姓名', trigger: 'blur'},
            {min: 2, max: 15, message: '长度在 2 到 15 个字符'}
          ],
          phone: [
            {required: true, message: '请输入手机号', trigger: 'blur'},
            {pattern: /^1[34578]\d{9}$/, message: '手机号只能为数字并且为11位的整数'}
          ]
        },
        editVal: [],
        indexData: []
      }
    },
    methods: {
      btnCacel (obj) {
        console.log(obj)
        this.dialogFormVisible = obj.msg
        if (obj.data !== '') {
          this.tableData.push({
            date: obj.data.date1,
            name: obj.data.name,
            phone: obj.data.phone,
            delivery: obj.data.delivery
          })
        }
      },
      changeFun (data) {
        console.log('val==>', data)
        this.editVal = data
        let _this = this
        data.forEach((val, index) => {
          _this.tableData.forEach((v, i) => {
            // id 是每一行的数据id
            if (val.phone === v.phone) {
              console.log('索引值', i)
              _this.indexData.push(i)
            }
          })
        })
      },
      removeData () {
        var _this = this
        if (this.editVal.length !== 0) {
          console.log('选中的数据', this.editVal)
          console.log('选中的索引值', this.indexData)
          _this.editVal.forEach((val, index) => {
            _this.tableData.forEach((v, i) => {
              // 这里应取id 是每一行的数据id
              if (val.phone === v.phone) {
                console.log(i)
                _this.tableData.splice(i, 1)
              }
            })
          })
        } else {
          alert('选中用户删除')
        }
      },
      btnFormVisible (data) {
        console.log(this.editVal)
        let _this = this
        if (this.editVal.length !== 0) {
          // _this.saveMsg = !_this.saveMsg
          if (!_this.saveMsg) {
            _this.editVal.forEach((val, index) => {
              _this.tableData.forEach((v, i) => {
                // 这里应取id 是每一行的数据id
                if (val.phone === v.phone) {
                  console.log(v.date2, v.name, v.phone)
                  if (v.date2 !== null && v.name !== '' && v.phone !== '') {
                    v.delivery = false
                    _this.saveMsg = true
                    _this.saveName = '编辑'
                    var date = v.date2
                    console.log('0' + (date.getMonth() + 1))
                    var month = date.getMonth() + 1 > 9 ? date.getMonth() + 1 : '0' + (date.getMonth() + 1)
                    var rdata = date.getDate() > 9 ? date.getDate() : '0' + date.getDate()
                    v.date1 = date.getFullYear() + '-' + month + '-' + rdata
                  } else {
                    v.delivery = true
                    _this.saveMsg = false
                    _this.saveName = '保存'
                  }
                }
              })
            })
          } else {
            _this.saveName = '保存'
            _this.editVal.forEach((val, index) => {
              _this.tableData.forEach((v, i) => {
                // 这里应取id 是每一行的数据id
                if (val.phone === v.phone) {
                  v.delivery = true
                  _this.saveMsg = false
                }
              })
            })
          }
        } else {
          alert('请选中用户编辑！！')
        }
      }
    },
    components: {
      'user-edit': UserEdit
    }
  }
</script>

<style scoped>
</style>
