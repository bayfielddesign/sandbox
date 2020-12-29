<template>
  <div id="app" role="main">
    <h1>User Registration Form</h1>
    <user-reg-form @user-added="addUser"></user-reg-form>
    <h2>Registered Users</h2>
    <ul>
      <li v-for="user in Users" :key="user.id">
        <user
          :fname="user.fname"
          :lname="user.lname"
          :eAddress="user.eAddress"
          :id="user.id"
        ></user>
      </li>
    </ul>
  </div>
</template>

<script>
import User from "./components/User.vue";
import uniqueId from "lodash.uniqueid";
import UserRegForm from "./components/UserRegForm";

export default {
  name: "app",
  components: {
    UserRegForm,
    User,
  },
  data() {
    return {
      Users: [
        {
          id: uniqueId("user-"),
          fname: "Clayton",
          lname: "Lamb",
          eAddress: "clamb@org.org",
        },
        {
          id: uniqueId("user-"),
          fname: "Madeline",
          lname: "Johnson",
          eAddress: "maddi@live.com",
        },
        {
          id: uniqueId("user-"),
          fname: "Wayne",
          lname: "Moody",
          eAddress: "wayne@moody.com",
        },
        {
          id: uniqueId("user-"),
          fname: "Lonnie",
          lname: "Hayes",
          eAddress: "lonnie.hayes@company.com",
        },
      ],
    };
  },
  methods: {
    addUser(fname, lname, eAddress, pwd) {
      this.Users.push({
        id: uniqueId("user-"),
        fname: fname,
        lname: lname,
        eAddress: eAddress,
        pwd: pwd,
      });
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  border-radius: 30px;
  background-color: #f2f2f2;
  padding: 20px;
}
h2 {
  text-align: left;
}
li {
  text-align: left;
  font-size: 20px;
}

input {
  width: 45%;
  height: 30px;
  border-radius: 5px;
  background-color: lightblue;
  margin-left: 2px;
  position: relative;
}

input:focus {
  background-color: white;
}

.form-label {
  display: inline-block;
  position: relative;
  width: 60%;
  margin: 20px 0px 0px;
  padding: 5px;
  font-size: 20px;
}

button {
  width: 20%;
  background-color:lightblue;
  font-size: 20px;
  padding: 14px 20px;
  margin: 8px;
  //border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  //background-color: blue;
  font-weight: bold;
  border: 2px solid black;
}


</style>