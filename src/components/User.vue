<template>
  <div>
    <label for="id">{{ fname }} {{ lname }}, {{ eAddress }}</label>
  </div>
</template>

<script>
//import uniqueId from "lodash.uniqueid";
export default {
  props: {
    fname: { required: true, type: String },
    lname: { required: true, type: String },
    eAddress: { required: true, type: String },
    pwd: { required: false, type: String },
    id: { required: true, type: String },
  },
};
</script>