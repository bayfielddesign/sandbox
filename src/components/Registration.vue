<template>
  <div class="container">
    <!--We are making a registartion form. Lets start with the basic html-->
    <!--We need a tile followed by 5 input fields and 2 buttons-->
    <!--We also need a text box to display a confirmation message and receipt-->
    <header>
      <h1>{{msg}}</h1>
    </header>
    <div id="content">
    <p>
      Please enter first name, last-name, email, password, and confirm password.
    </p>
    <!--This will be displayed as a single coloum, TODO: make into a table-->
    <form name="register">
      <label for="firstname">First Name: </label>
      <input type="text" id="firstname"/>
      <br>
      <label for="lastname">Last Name: </label>
      <input type="text" id="lastname"/>
      <br>
      <label for="email">Email: </label>
      <input type="email" id="email"/>
      <br>
      <label for="password">Password: </label>
      <input type="password" id="password"/>
      <br>
      <label for="confirmpassword">Confirm Password: </label>
      <input type="password" id="confirmpassword"/>
      <br>
      <button type="reset">Reset</button>
      <button type="submit">Submit</button>
    </form>
    <div hidden>confirmation and receipt</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Registration',
  props: {
    msg: String
  },
  data () {
    return {
    }
  },
  methods: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
