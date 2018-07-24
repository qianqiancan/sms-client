<template>
  <!-- Content Wrapper. Contains page content -->
  <div id="content-wrap" class="content-wrapper">
    <row class="ndy-rwo-padd">
      <div class="col-md-12">
        <user-header></user-header>
      </div>
    </row>
    <!-- Content Header (Page header) -->
    <!--<section class="content-header">-->
      <!--<ol class="breadcrumb">-->
        <!--<li><a href="#"><i class="fa fa-dashboard"></i> Home</a></li>-->
        <!--<li class="active">Dashboard</li>-->
      <!--</ol>-->
    <!--</section>-->

    <section class="content">
      <transition name="page" mode="out-in">
        <router-view></router-view>
      </transition>
    </section>
    <!-- /.content -->
  </div>
  <!-- /.content-wrapper -->
</template>

<script>
  // 头部
  import UserHeader from 'examples/UserHeader.vue'
  export default {
    components: {
      'user-header': UserHeader
    },
    name: 'va-content-wrap',
    created () {

    }
  }
</script>

<style>
.page-enter-active, .page-leave-active {
  transition: opacity 0.5s, transform 0.5s;
}
.page-enter, .page-leave-to {
  opacity: 0;
}
.ndy-rwo-padd {
  padding: 30px;
}
</style>
