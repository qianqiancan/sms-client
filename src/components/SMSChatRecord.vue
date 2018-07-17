<template>
  <row>
    <div class="col-md-4">
      显示用户列表
    </div>
    <div class="col-md-8">
      <va-direct-chat
        theme="primary"
        :talkList="talkList"
        :contacts="contacts"
        title="短信来往"
        :badgeCount="30"
        placeholder=""
      ></va-direct-chat>
    </div>
  </row>
</template>

<script>
  import VADirectChat from '../widgets/VADirectChat.vue'
  export default {
      // name: 'sms-chat-record',
    data () {
      return {
        talkList: [
          {
            name: 'Alexander Pierce',
            date: new Date(),
            profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
            message: `Is this template really for free? That's unbelievable`,
            isMine: false
          },
          {
            name: 'Sarah Bullock',
            date: new Date(),
            profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
            message: `You better believe it!`,
            isMine: true
          }
        ]
      }
    },
    components: {
      'va-direct-chat': VADirectChat
    }
  }
</script>

<style>

</style>
