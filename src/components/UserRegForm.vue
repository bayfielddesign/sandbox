<template>
  <form>
    <label for="fname" class="form-label"> First Name: </label>
    <input
      type="text"
      id="fname"
      name="fname"
      autocomplete="off"
      v-model.lazy.trim="fname"
    /><br />
    <label for="lname" class="form-label"> Last Name: </label>
    <input
      type="text"
      id="lname"
      name="lname"
      autocomplete="off"
      v-model.lazy.trim="lname"
    /><br />
    <label for="eAddress" class="form-label"> Email Address: </label>
    <input
      type="email"
      id="eAddress"
      name="eAddress"
      autocomplete="off"
      v-model.lazy.trim="eAddress"
    /><br />
    <label for="pwd" class="form-label"> Password: </label>
    <input
      type="password"
      id="pwd"
      name="pwd"
      autocomplete="off"
      v-model.lazy.trim="pwd"
    /><br />
    <label for="pwd2" class="form-label"> Confirm Password: </label>
    <input
      type="password"
      id="pwd2"
      name="pwd2"
      autocomplete="off"
      v-model.lazy.trim="pwd2"
    /><br />
    <button v-on:click.prevent="clear">Clear</button>
    <button v-on:click.prevent="onSubmit">Submit</button>
  </form>
</template>

<script>
export default {
  methods: {
    onSubmit() {
      if (this.fname === "") {
        alert("First name is required");
        return;
      } else if (this.lname === "") {
        alert("Last name is required");
        return;
      } else if (this.eAddress.includes("@") == false || this.eAddress === "") {
        alert("Email address is required and must include the @ symbol");
        return;
      } else if (this.pwd === "" || this.pwd !== this.pwd2) {
        alert("Password is required and both passwords must match");
        return;
      }
      this.$emit("user-added", this.fname, this.lname, this.eAddress, this.pwd);
      alert("User added successfully");
      this.fname = "";
      this.lname = "";
      this.eAddress = "";
      this.pwd = "";
      this.pwd2 = "";
    },
    clear() {
      console.log("clear clicked");
      this.fname = "";
      this.lname = "";
      this.eAddress = "";
      this.pwd = "";
      this.pwd2 = "";
    },
  },
  data() {
    return {
      fname: "",
      lname: "",
      eAddress: "",
      pwd: "",
      pwd2: "",
    };
  },
};
</script>