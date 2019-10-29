<template>
  <div>
    <div class="card m-2" style="width: 40rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="thecardtitle"></h5>
        <button @click="sendMessage" class="btn btn-info">Send Child A Message</button>
        <componentChild :parentmessage="parentmessage" @finished="finished"></componentChild>
      </div>
    </div>
  </div>
</template>
<script>
import componentChild from "./childComponent/componentChild.vue";
export default {
  components: {
    componentChild
  },
  data() {
    return {
      thecardtitle: "Parent Component!",
      parentmessage: ""
    };
  },

  methods: {
    sendMessage() {
      this.parentmessage = "<b>Message From Parent:</b> Do Your Homework";
    },

    finished(){
        this.parentmessage = '';
    }
  }
};
</script>