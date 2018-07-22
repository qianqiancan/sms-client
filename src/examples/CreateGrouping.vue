<template>
  <div class="dashboard">
    <h2></h2>
    <row>
      <el-form :model="form" :rules="rules" ref="create">
        <el-form-item label="分组名" :label-width="formLabelWidth"  prop="name">
          <el-input v-model="form.name" auto-complete="off"></el-input>
        </el-form-item>
        <!--<el-form-item label="日期" :label-width="formLabelWidth" prop="date2">-->
          <!--<el-date-picker type="date" placeholder="选择日期" v-model="form.date2">-->
          <!--</el-date-picker>-->
        <!--</el-form-item>-->
        <!--<el-form-item label="姓名" :label-width="formLabelWidth"  prop="name">-->
          <!--<el-input v-model="form.name" auto-complete="off"></el-input>-->
        <!--</el-form-item>-->
        <!--<el-form-item label="电话" :label-width="formLabelWidth" prop="phone">-->
          <!--<el-input v-model="form.phone">-->
          <!--</el-input>-->
        <!--</el-form-item>-->
        <el-form-item class="text-center">
          <el-button @click="btnCacel(1)" type="primary">添加</el-button>
          <el-button @click="btnCacel(2)">取消</el-button>
        </el-form-item>
      </el-form>
    </row>
  </div>
</template>

<script>
  export default {
    props: {
      newMsg: '',
      formVal: ''
    },
    data: function () {
      return {
        form: {
          name: '组名2',
          neWshow: false,
          bgColor: 'bg-yellow',
          // 当前数据ID
          codeId: Math.floor(Math.random() * 10 + 1)
        },
        rules: {
          date2: [
            {type: 'string', required: true, message: '请选择日期', trigger: 'change'}
          ],
          name: [
            {type: 'string', required: true, message: '请输入姓名', trigger: 'blur'},
            {min: 1, max: 15, message: '长度在 2 到 15 个字符'}
          ],
          phone: [
            {type: 'string', required: true, message: '请输入手机号', trigger: 'blur'},
            {pattern: /^1[34578]\d{9}$/, message: '手机号只能为数字并且为11位的整数'}
          ]
        },
        formLabelWidth: '120px'
      }
    },
    methods: {
      btnCacel (mun) {
        if (mun === 1) {
          // 主动校验
          this.$refs.create.validate((valid) => {
            if (valid) {
              this.$emit('edit-content', { status: false, content: this.form })
            }
          })
        } else {
          this.$emit('edit-content', { status: false, content: '' })
        }
      }
    }
  }
</script>

<style scoped>

</style>
