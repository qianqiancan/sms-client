<template>
  <el-table
    ref="table"
    @selection-change="changeFun"
    v-if="userMsg"
    :data="userData"
    border
    style="width: 100%">
    <el-table-column
      type="selection"
      width="55">
    </el-table-column>
    <el-table-column
      prop="grouping"
      label="分组"
      width="180">
    </el-table-column>
    <el-table-column
      prop="name"
      label="姓名"
      width="180">
    </el-table-column>
    <el-table-column
      prop="phone"
      label="手机号">
    </el-table-column>
  </el-table>
</template>

<script>
  export default {
    props: {
      userMsg: '',
      userData: {}
    },
    data () {
      return {
        // 选中的手机号集合
        phones: [],
        // 选中的分组集合
        groupings: [],
        // 选中的索引值集合
        userIndex: []
        // sendMastion: {
        //   id: '666',
        //   name: 'admin',
        //   phones: [],
        //   content: '',
        //   date: new Date(),
        //   groupings: []
        // }
      }
    },
    methods: {
      // 选中的用户
      changeFun (data) {
        let _this = this
        _this.phones = []
        _this.groupings = []
        // _this.userIndex = []
        data.forEach((val, index) => {
          _this.userData.forEach((v, i) => {
            // id 是每一行的数据id
            if (val.id === v.id) {
              // _this.userIndex.push(i)
              _this.phones.push(v.phone)
              _this.groupings.push(v.grouping)
            }
          })
        })
        this.$emit('btn-select', { arrPhone: _this.phones, arrGroupings: _this.groupings })
      },
      checked () {
        // 首先el-table添加ref="table"引用标识
        // var _this = this
        // _this.$refs.table.toggleRowSelection(this.userData[0], true)
        // _this.userData.forEach((val, index) => {
        //   _this.$refs.table.toggleRowSelection(this.userData[val], true)
        // })
      }
    },
    mounted () {
      // var _this = this
      // this.$watch('userData', function () {
      //   _this.checked()
      // })
    }
  }
</script>
