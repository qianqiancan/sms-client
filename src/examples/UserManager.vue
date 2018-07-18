<template>
  <section class="content">
    <row>

      <div class="col-md-12 col-sm-12 col-xs-12">
        <el-button @click="dialogFormVisible = true" plain>新增</el-button>
        <el-button type="primary" plain>导入</el-button>
        <el-button type="primary" @click="dialogFormEdit = true" plain>编辑</el-button>
        <el-button type="success" @click="removeData" plain>删除</el-button>
        <el-button type="danger" @click="tableData = []" plain>全部删除</el-button>
      </div>
    </row>
    <row>
      <div class="col-md-12 col-sm-12 col-xs-12">
        <el-table
          @selection-change="changeFun"
          :data="tableData"
          style="width: 100%"
          :row-class-name="tableRowClassName">
          <el-table-column
            type="selection"
            width="55">
          </el-table-column>
          <el-table-column
            prop="date"
            label="日期"
            width="180">
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180">
          </el-table-column>
          <el-table-column
            prop="phone"
            label="电话">
          </el-table-column>
        </el-table>
      </div>
    </row>
    <el-dialog title="新增用户" :visible.sync="dialogFormVisible">
      <user-edit @btn-cacel="btnCacel" @btn-deter="btnCacel"></user-edit>
    </el-dialog>
    <el-dialog title="编辑用户" :visible.sync="dialogFormEdit">
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
          dialogFormEdit: false,
          tableData: [{
            id: 1,
            date: '2016-05-02',
            name: '王小虎',
            phone: '13333333333'
          }, {
            id: 2,
            date: '2016-05-04',
            name: '王小虎',
            phone: '13222222222'
          }, {
            id: 3,
            date: '2016-05-01',
            name: '王小虎',
            phone: '13111111111'
          }, {
            id: 4,
            date: '2016-05-03',
            name: '王小虎',
            phone: '13444444444'
          }],
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
              phone: obj.data.phone
            })
          }
        },
        changeFun (data) {
          console.log('val==>', data)
          this.editVal.push(data)
          let _this = this
          data.forEach((val, index) => {
            _this.tableData.forEach((v, i) => {
              // id 是每一行的数据id
              if (val.id === v.id) {
                console.log('索引值', i)
                _this.indexData.push(i)
              }
            })
          })
        },
        removeData () {
          console.log('选中的数据', this.editVal)
          console.log('选中的索引值', this.indexData)
        }
      },
      components: {
        'user-edit': UserEdit
      }
    }
</script>

<style scoped>
</style>
