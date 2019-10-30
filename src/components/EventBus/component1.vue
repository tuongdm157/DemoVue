
<template>
  <div>
    <div class="card m-3" style="width: 20rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="thecardtitle"></h5>
        <p class="card-text" v-html="thecardbody"></p>
        <div v-if="message" class="card-text alert alert-warning" v-html="message"></div>
        <div class="d-flex justify-content-center">
          <button @click="onClickSendMessageToChild2" class="btn btn-danger">Message To Child 2</button>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script>
import { eventBus } from "../../main";
export default {
  data() {
    return {
      thecardtitle: "Child Component!",
      thecardbody: "ComponentChild1",
      message: ""
    };
  },

  created() {
    eventBus.$on("messageFromComponent2", message => {
      this.message = message;
    });
  },
  methods: {
    onClickSendMessageToChild2() {
      eventBus.$emit(
        "messageFromComponent1",
        "<b>This is message from component1</b>"
      );
    }
  }
};
</script>
 