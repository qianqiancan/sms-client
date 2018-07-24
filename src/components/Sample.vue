<template>
  <!-- Info boxes -->
  <section class="content">
    <!--<row>-->
      <!--<div v-for="item in indexes" class="col-md-3 col-sm-6 col-xs-12">-->
        <!--<div class="info-box">-->
          <!--<span v-bind:class="item.clazz2" ><i v-bind:class="item.clazz"></i></span>-->

          <!--<div class="info-box-content">-->
            <!--<span class="info-box-text">{{item.name}}</span>-->
            <!--<span class="info-box-number">{{item.count}}</span>-->
          <!--</div>-->
          <!--&lt;!&ndash; /.info-box-content &ndash;&gt;-->
        <!--</div>-->
      <!--</div>-->
    <!--</row>-->
    <!-- /.row -->


    <row>
      <div class="col-md-8">
          <p class='text-center'>
            <strong>短信发送情况统计</strong>
          </p>
          <va-chart
            :chart-config='barChartConfig'
          >
          </va-chart>
        <!-- /.box -->
      </div>
      <div class="col-md-4">
        <sms-record-box v-for="item in messages"
                        v-bind:wrap-bg-color="item.wrapBgColor"
                        v-bind:bg-icon="item.bgIcon"
                        v-bind:text="item.text"
                        v-bind:number="item.number"
                        v-bind:is-progress="item.isProgress"
                        v-bind:number-type="item.numberType"
                        v-bind:sender="item.sender"
                        v-bind:percentage="item.percentage"
        ></sms-record-box>
      </div>
    </row>
    <!-- /.row -->
  </section>
</template>

<script>
  import VAChart from '../components/VAChart'
  import SMSRecordBox from '../widgets/SMSRecordBox'

  var data = {
    // indexes: [
    //   {
    //     clazz: 'ion ion-ios-gear-outline',
    //     clazz2: 'info-box-icon bg-aqua',
    //     name: '用户1',
    //     count: 20
    //   },
    //   {
    //     clazz: 'fa fa-google-plus',
    //     clazz2: 'info-box-icon bg-red',
    //     name: '用户2',
    //     count: 20
    //   },
    //   {
    //     clazz: 'ion ion-ios-cart-outline',
    //     clazz2: 'info-box-icon bg-green',
    //     name: '用户3',
    //     count: 20
    //   },
    //   {
    //     clazz: 'ion ion-ios-people-outline',
    //     clazz2: 'info-box-icon bg-yellow',
    //     name: '用户4',
    //     count: 20
    //   }
    // ],
    barChartConfig: {
      type: 'bar',
      data: {
        labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July'],
        datasets: [
          {
            label: '发送短信数',
            backgroundColor: [
              'rgba(255, 99, 132, 0.2)',
              'rgba(54, 162, 235, 0.2)',
              'rgba(255, 206, 86, 0.2)',
              'rgba(75, 192, 192, 0.2)',
              'rgba(153, 102, 255, 0.2)',
              'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
              'rgba(255,99,132,1)',
              'rgba(54, 162, 235, 1)',
              'rgba(255, 206, 86, 1)',
              'rgba(75, 192, 192, 1)',
              'rgba(153, 102, 255, 1)',
              'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1,
            data: [65, 59, 80, 81, 56, 55, 40]
          }
        ]
      },
      options: {
        scales: {
          xAxes: [{
            stacked: true
          }],
          yAxes: [{
            stacked: true
          }]
        }
      }
    },
    messages: [
      {
        wrapBgColor: 'bg-yellow',
        bgIcon: 'ion ion-ios-pricetag-outline',
        text: '短信内容1111111短信内容',
        number: 5200,
        isProgress: true,
        numberType: 'comma',
        sender: '张三',
        percentage: 50
      },
      {
        wrapBgColor: 'bg-green',
        bgIcon: 'ion ion-ios-pricetag-outline',
        text: '短信内容短信内容2222',
        number: 92050,
        isProgress: true,
        numberType: 'comma',
        sender: '李四',
        percentage: 20
      },
      {
        wrapBgColor: 'bg-yellow',
        bgIcon: 'ion ion-ios-pricetag-outline',
        text: '短信内容1111111',
        number: 5200,
        isProgress: true,
        numberType: 'comma',
        sender: '张三',
        percentage: 50
      },
      {
        wrapBgColor: 'bg-green',
        bgIcon: 'ion ion-ios-pricetag-outline',
        text: '短信内容短信内容2222',
        number: 92050,
        isProgress: true,
        numberType: 'comma',
        sender: '李四',
        percentage: 20
      }
    ]
  }
  export default {
    name: 'sample',
    components: {
      'va-chart': VAChart,
      'sms-record-box': SMSRecordBox
    },
    data () {
      return data
    },
    created () {
    }
  }
</script>
