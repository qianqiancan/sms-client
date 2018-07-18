<template>
  <div>


    <row>
      <div class="col-md-4">
        <row>
          <div class="col-md-12 col-sm-12 col-xs-12">
            <el-button type="success">添加</el-button>
            <el-button type="success">删除</el-button>
          </div>
        </row>
        <sms-group-item v-for="item in messages"
                        v-bind:wrap-bg-color="item.wrapBgColor"
                        v-bind:bg-icon="item.bgIcon"
                        v-bind:name="item.name">

        </sms-group-item>
      </div>
      <div class="col-md-8">

      </div>
    </row>
  </div>
</template>

<script>
  import VaText from '../components/VAText'
  import SmsGroupItem from '../widgets/SmsGroupItem'
  export default {
    components: {
      'sms-group-item': SmsGroupItem,
      'va-text': VaText
    },
    data: function () {
      return {
        messages: [
          {
            wrapBgColor: 'bg-yellow',
            bgIcon: 'ion ion-ios-pricetag-outline',
            name: '组名1'
          },
          {
            wrapBgColor: 'bg-green',
            bgIcon: 'ion ion-ios-pricetag-outline',
            name: '组名2'
          }
        ]
      }
    }
  }
</script>

<style scoped>

</style>
