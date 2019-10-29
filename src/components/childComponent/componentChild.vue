
<template>
  <div>
    <div class="card m-3" style="width: 25rem;">
      <div class="card-body">
        <h5 class="card-title" v-text="thecardtitle"></h5>
        <p class="card-text" v-html="thecardbody"></p>
        <div v-if="parentmessage" class="card-text alert alert-warning" v-html="parentmessage"></div>
        <button v-if="parentmessage" @click="onClick" class="btn btn-success">Ok</button>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  props: ["parentmessage"],
  data() {
    return {
      thecardtitle: "Child Component!",
      thecardbody: "I'm just a child."
    };
  },
  methods: {
    onClick() {
      this.$emit("finished");
    }
  }
};
</script>
 