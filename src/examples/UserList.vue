<template>
  <div>
    <el-table
      :data="content"
      height="250"
      style="width: 100%"
      :default-sort = "{prop: 'date', order: 'descending'}"
      @selection-change="changeFun"
    >
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
  </div>
</template>
<script>
  export default {
    props: {
      content: {}
    },
    data () {
      return {
      }
    },
    methods: {
      changeFun (data) {
        this.$emit('new-content', data)
      }
    }
  }
</script>
