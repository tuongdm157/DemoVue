
<template>
  <div>
    <div class="card m-3" style="width: 20rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="thecardtitle"></h5>
        <p class="card-text" v-html="thecardbody"></p>
        <div v-if ="message" class="card-text alert alert-warning" v-html="message"></div>
        <div class="d-flex justify-content-center">
          <button @click="onClickSendMessageToChild1" class="btn btn-danger">Message To Child 1</button>
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
      thecardbody: "ComponentChild2",
      message: ''
    };
  },

  created() {
    eventBus.$on("messageFromComponent1", message => {
      this.message = message;
    });
  },

  methods: {
    onClickSendMessageToChild1() {
        eventBus.$emit('messageFromComponent2', '<b>This is message from component2</b>')
    }
  }
};
</script>
 