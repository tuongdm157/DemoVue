
<template>
  <div>
    <div class="card m-3" style="width: 20rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="thecardtitle"></h5>
        <p class="card-text" v-html="thecardbody"></p>
        <div v-if="parentmessage" class="card-text alert alert-warning" v-html="parentmessage"></div>
        <div
          v-if="messageFromChild2"
          class="card-text alert alert-warning"
          v-html="messageFromChild2"
        ></div>
        <div class="d-flex justify-content-center">
          <button v-if="parentmessage" @click="onClick" class="btn btn-success mr-2">OK</button>
          <button
            v-if="parentmessage"
            @click="onClickSendMessageToChild2"
            class="btn btn-danger"
          >Message To Child 2</button>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  props: ["parentmessage", "messageFromChild2"],
  data() {
    return {
      thecardtitle: "Child Component!",
      thecardbody: "ComponentChild1"
    };
  },
  methods: {
    onClick() {
      this.$emit("finished");
    },

    onClickSendMessageToChild2() {
      this.$emit(
        "onClickSendMessageToChild2",
        "Message from Component Child 1"
      );
    }
  }
};
</script>
 