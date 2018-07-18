<template>
  <section class="content">
    <row>

      <div class="col-md-12 col-sm-12 col-xs-12">
        <el-button @click="dialogFormVisible = true" plain>新增</el-button>
        <el-button type="primary" plain>导入</el-button>
        <el-button type="success" plain>删除</el-button>
        <el-button type="danger" plain>全部删除</el-button>
      </div>
    </row>
    <row>
      <div class="col-md-12 col-sm-12 col-xs-12">
        <el-table
          :data="tableData"
          style="width: 100%">
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
            prop="address"
            label="地址">
          </el-table-column>
        </el-table>
      </div>
    </row>
    <el-dialog title="新增用户" :visible.sync="dialogFormVisible">
      <el-form :model="form">
        <el-form-item label="姓名" :label-width="formLabelWidth">
          <el-input v-model="form.name" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="电话" :label-width="formLabelWidth">
          <el-input v-model="form.phone" >
          </el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary">确定</el-button>
          <el-button>取消</el-button>
        </el-form-item>
      </el-form>
    </el-dialog>
  </section>

</template>

<script>

    export default {
      data: function () {
        return {
          tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }],
          dialogFormVisible: false,
          form: {
            name: '',
            phone: '',
            date1: '',
            date2: '',
            delivery: false,
            type: [],
            resource: '',
            desc: ''
          },
          formLabelWidth: '120px'
        }
      },
      methods: {
      },
      components: {
      }
    }
</script>

<style scoped>

</style>
