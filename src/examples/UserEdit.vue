<template>
  <div class="dashboard">
    <row>
      <el-form :model="form">
        <el-form-item label="姓名" :label-width="formLabelWidth">
          <el-input v-model="form.name" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="电话" :label-width="formLabelWidth">
          <el-input v-model="form.phone">
          </el-input>
        </el-form-item>
        <el-form-item>
          <el-button @click="btnCacel(1)" type="primary">确定</el-button>
          <el-button @click="btnCacel(2)">取消</el-button>
        </el-form-item>
      </el-form>
    </row>
  </div>
</template>
<script>
  export default {
    data: function () {
      return {
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
      tableRowClassName: function ({row, rowIndex}) {
        if (rowIndex % 2 === 1) {
          return 'warning-row'
        }
        return 'success-row'
      },
      btnCacel (mun) {
        var date = new Date()
        console.log('0' + (date.getMonth() + 1))
        var month = date.getMonth() + 1 > 9 ? date.getMonth() + 1 : '0' + (date.getMonth() + 1)
        var rdata = date.getDate() > 9 ? date.getDate() : '0' + date.getDate()
        this.form.date1 = date.getFullYear() + '-' + month + '-' + rdata
        this.$emit('btn-cacel', { msg: false, data: mun === 1 ? this.form : '' })
        this.form.name = ''
        this.form.phone = ''
      }
    },
    components: {
    }
  }
</script>

<style scoped>

</style>
