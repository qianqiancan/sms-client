<template>
  <div class="info-box" :class="wrapBgColor">
    <span class="info-box-icon" v-bind:class="bgColor">
      <i v-bind:class="bgIcon"></i>
    </span>
    <div class="info-box-content">
      <span class="message">{{name}}</span>
    </div>
  </div>
</template>
<style>
  .message {
    display:block;
    font-size:16px;
    white-space:nowrap;
    overflow: no-display;
    text-overflow:ellipsis;
    height: 20px
  }

  .sender {
    margin: 0;
    font-size: 10px;
    float: right;

  }
</style>
<script>
  export default {
    props: {
      'wrapBgColor': {
        type: String
      },
      'bgColor': {
        type: String
      },
      'bgIcon': {
        type: String
      },
      'name': {
        type: String,
        required: true
      }
    },
    computed: {
      parseNumber () {
        let result = this.number
        // FIXME: using constant
        switch (this.numberType) {
          case 'percentage':
            result += '%'
            break
          case 'comma':
            result = Number(result).toLocaleString('en')
            break
          default:
            break
        }
        return result
      }
    }
  }
</script>

<style scoped>

</style>
