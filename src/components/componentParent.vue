<template>
  <div>
    <div class="card m-2" style="width: 60rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="thecardtitle"></h5>
        <button @click="sendMessage" class="btn btn-info">Send Child A Message</button>
        <div class="d-flex justify-content-center">
          <componentChild1
            :parentmessage="parentmessage"
            @finished="finished"
            @onClickSendMessageToChild2="onClickSendMessageToChild2"
            :messageFromChild2="messageFromChild2"
          ></componentChild1>
          <component-child2
            :parentmessage="parentmessage"
            :messageFromChild1="messageFromChild1"
            @sendMessageToChild1="sendMessageToChild1"
          />
        </div>
        <div class="d-flex justify-content-center">
          <component1-e-b></component1-e-b>
          <component2-e-b></component2-e-b>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import componentChild1 from "./childComponent/componentChild1.vue";
import componentChild2 from "./childComponent/componentChild2.vue";
import Component1EB from "./EventBus/component1.vue";
import Component2EB from "./EventBus/component2.vue";
export default {
  components: {
    componentChild1,
    componentChild2,
    Component1EB,
    Component2EB
  },
  data() {
    return {
      thecardtitle: "Parent Component!",
      parentmessage: "",
      messageFromChild1: "",
      messageFromChild2: ""
    };
  },

  methods: {
    sendMessage() {
      this.parentmessage = "<b>Message From Parent:</b> Do Your Homework";
    },

    finished() {
      this.parentmessage = "";
    },

    onClickSendMessageToChild2(message) {
      this.messageFromChild1 = message;
    },

    sendMessageToChild1(message) {
      console.log(message);
      this.messageFromChild2 = message;
    }
  }
};
</script>