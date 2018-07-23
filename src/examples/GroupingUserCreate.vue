<template>
  <div class="dashboard">
    <!--添加用户-->
    <row>
      <!--ref="table  在el-table 中添加该属性配合默认勾选状态-->
      <el-table
        @selection-change="changeFun"
        :data="userList"
        height="500"
        style="width: 100%"
        :default-sort = "{prop: 'date', order: 'descending'}"
      >
      <!--:selectable="checkSelectable" el-table-colum 中添加该属性配合默认禁用状态-->
        <el-table-column
          type="selection"
          width="55">
        </el-table-column>
        <el-table-column
          type="index"
          label="序号"
          width="100"
          sortable>
        </el-table-column>
        <el-table-column
          property="date"
          label="日期"
          width="180"
          sortable>
        </el-table-column>
        <el-table-column
          prop="name"
          label="姓名"
          width="180"
          sortable>
        </el-table-column>
        <el-table-column
          prop="address"
          label="地址"
          sortable>
        </el-table-column>
      </el-table>
      <div class="col-md-12 text-center" style="margin-top: 20px">
        <el-button @click="CreateData(1)" type="primary">添加</el-button>
        <el-button @click="CreateData(2)">取消</el-button>
      </div>
    </row>
  </div>
</template>
<script>
  export default {
    props: {
      defaultIndex: [],   // 默认显示第几个勾选中
      userList: []      // 数据
    },
    data: function () {
      return {
        arrUserData: []    // 选中的元素
      }
    },
    methods: {
      changeFun (data) {
        this.arrUserData = data
      },
      CreateData (mun) {
        this.$emit('btn-user-data', { msg: false, userObj: mun === 1 ? this.arrUserData : [] })
        this.userList = []
        this.arrUserData = []
      },
      // 默认勾选方法
      checked () {
        // var _this = this
        // 首先el-table添加ref="table"引用标识
        // this.defaultIndex.forEach((val, index) => {
          // _this.$refs.table.toggleRowSelection(this.userList[val], true)
        // })
      },
      // 默认禁用勾选方法   这个方法会默认调用两次   没找到原因
      checkSelectable (row, index) {
        // console.log(row, index
        // this.defaultIndex.forEach((val, index) => {
        //   console.log(val)
          // console.log(index !== val)
          // return index !== val
        // })
        // return index === 1
      }
    },
    mounted () {
      // 每次更新了数据，触发这个函数即可。
      // this.$nextTick(function () {
      //   this.checked()
      // })
    }
  }
</script>

<style scoped>

</style>
