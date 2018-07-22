<template>
  <div>
    <row>
      <div v-for="item in indexes" class="col-md-3 col-sm-6 col-xs-12">
        <div class="info-box">
          <span v-bind:class="item.clazz2" ><i v-bind:class="item.clazz"></i></span>

          <div class="info-box-content">
            <span class="info-box-text">{{item.name}}</span>
            <span class="info-box-number">{{item.count}}</span>
          </div>
          <!-- /.info-box-content -->
        </div>
      </div>
    </row>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        indexes: [
          {
            clazz: 'ion ion-ios-gear-outline',
            clazz2: 'info-box-icon bg-aqua',
            name: '用户1',
            count: 20
          },
          {
            clazz: 'fa fa-google-plus',
            clazz2: 'info-box-icon bg-red',
            name: '用户2',
            count: 20
          },
          {
            clazz: 'ion ion-ios-cart-outline',
            clazz2: 'info-box-icon bg-green',
            name: '用户3',
            count: 20
          },
          {
            clazz: 'ion ion-ios-people-outline',
            clazz2: 'info-box-icon bg-yellow',
            name: '用户4',
            count: 20
          }
        ]
      }
    }
  }
</script>
