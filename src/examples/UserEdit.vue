<template>
  <div class="dashboard">
    <row>
      <el-form :model="form" :rules="rules" ref="create">
        <el-form-item label="日期" :label-width="formLabelWidth" prop="date2">
          <el-date-picker type="date" placeholder="选择日期" v-model="form.date2">
          </el-date-picker>
        </el-form-item>
        <el-form-item label="姓名" :label-width="formLabelWidth" prop="name">
          <el-input v-model="form.name" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="电话" :label-width="formLabelWidth" prop="phone">
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
          date2: new Date(),
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
        rules: {
          date2: [
            {type: 'date', required: true, message: '请选择日期', trigger: 'change'}
          ],
          name: [
            {required: true, message: '请输入姓名', trigger: 'blur'},
            {min: 3, max: 15, message: '长度在 2 到 15 个字符'}
          ],
          phone: [
            {required: true, message: '请输入手机号', trigger: 'blur'},
            {pattern: /^1[34578]\d{9}$/, message: '手机号只能为数字并且为11位的整数'}
          ]
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
        if (mun === 1) {
          var date = this.form.date2
          console.log('0' + (date.getMonth() + 1))
          var month = date.getMonth() + 1 > 9 ? date.getMonth() + 1 : '0' + (date.getMonth() + 1)
          var rdata = date.getDate() > 9 ? date.getDate() : '0' + date.getDate()
          this.form.date1 = date.getFullYear() + '-' + month + '-' + rdata
          // 主动校验
          this.$refs.create.validate((valid) => {
            console.log('valid', valid)
            if (valid === true) {
              this.$emit('btn-cacel', { msg: false, data: mun === 1 ? this.form : '' })
              this.form.name = ''
              this.form.phone = ''
            } else {
              this.$emit('btn-cacel', { msg: true, data: '' })
            }
          })
        } else {
          this.$emit('btn-cacel', { msg: false, data: mun === 1 ? this.newMsg ? this.form : this.formVal : '' })
          this.form.name = ''
          this.form.phone = ''
        }
      }
    },
    components: {
    }
  }
</script>

<style scoped>

</style>
