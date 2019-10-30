<template>
  <div>
    <div class="card m-3" style="width: 20rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="theCardTitle"></h5>
        <p class="card-text" v-html="theCardBody"></p>
        <div
          v-if="messageFromChild1"
          class="card-text alert alert-warning"
          v-html="messageFromChild1"
        ></div>
        <button
          v-if="messageFromChild1"
          class="btn btn-success"
          @click="sendMessageToChild1"
        >Message To Child1</button>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  props: ["messageFromChild1"],
  data() {
    return {
      theCardTitle: "Child Component!",
      theCardBody: "ComponentChild2"
    };
  },
  methods: {
    sendMessageToChild1() {
      this.$emit("sendMessageToChild1", "Message From Component Child2");
    }
  }
};
</script>