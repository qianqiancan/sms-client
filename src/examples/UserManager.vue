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
          style="width: 100%"
          :row-class-name="tableRowClassName">
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
      <user-edit></user-edit>
    </el-dialog>
  </section>

</template>

<script>
    import UserEdit from './UserEdit.vue'
    export default {
      data: function () {
        return {
          dialogFormVisible: false,
          tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            phone: '13333333333'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            phone: '13222222222'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            phone: '13111111111'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            phone: '13444444444'
          }]
        }
      },
      methods: {
      },
      components: {
        'user-edit': UserEdit
      }
    }
</script>

<style scoped>
</style>
