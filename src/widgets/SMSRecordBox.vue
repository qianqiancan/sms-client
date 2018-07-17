<template>
  <div class="info-box" :class="wrapBgColor">
    <span class="info-box-icon" v-bind:class="bgColor">
      <i v-bind:class="bgIcon"></i>
    </span>
    <div class="info-box-content">
      <span class="message">{{text}}</span>
      <!--<span class="info-box-number">{{parseNumber}}</span>-->

      <!--<div class="progress" v-if="isProgress">-->
        <!--<div class="progress-bar" :style="`width: ${percentage}%`"></div>-->
      <!--</div>-->
      <span class="sender">
        {{ sender }}
      </span>
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
    height: 60px
  }

  .sender {
    margin: 0;
    font-size: 10px;
    float: right;

  }
</style>
<script>
    export default {
      name: 'sms-record-box',
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
        'text': {
          type: String,
          required: true
        },
        'number': {
          type: String,
          default: 0
        },
        'numberType': {
          type: String
        },
        'percentage': {
          type: Number,
          default: 0
        },
        'sender': {
          type: String,
          default: ''
        },
        'isProgress': {
          type: Boolean,
          default: false
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
