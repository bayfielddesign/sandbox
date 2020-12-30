<!--
 * @file   This files contains the Basic Registration Form component.
 * @author Lucas Roes.
 * Created: December 27, 2020.
 -->

<template>
  <div class="form">
    <div id="RegForm" v-if="showForm">
      <h1 id="Title" >Sign Up</h1>
      <hr>
      <form v-on:submit.prevent="submitForm">

        <label for="fname">First Name:</label>
        <input
          v-model="user.fname"
          type="text"
          id="fname"
          placeholder="Alice"
          required
        >

        <label for="lname">Last Name:</label>
        <input
          v-model="user.lname"
          type="text"
          id="lname"
          placeholder="Bob"
          required
        >

        <label for="email">Email:</label>
        <input
          v-model="user.email"
          type="email"
          id="email"
          placeholder="AliceBob@email.com"
          required
        >

        <label for="password">Password:</label>
        <input
          v-model="user.password"
          v-on:keyup.prevent="checkPassword"
          type="password"
          id="password"
          required
        >

        <label for="confirmPassword">Confirm Password:</label>
        <input
          v-model="user.passwordConfirm"
          v-on:keyup.prevent="checkPassword"
          type="password"
          id="confirmPassword"
          required
        >
        <span id='errorMessage' v-show="showErrorMessage">{{errorMessage}}</span>
        <div class="buttons">
          <button class="secondary button" type="button" v-on:click.prevent="clearForm">Clear</button>
          <input class="mainbtn button" type="submit" value="Submit">
        </div>
      </form>
    </div>

    <div id="Receipt" v-if="showReceipt">
      <h1>Congratulations!</h1>
      <h2>You have signed up!</h2>
      <hr>

      <p>Name: {{ this.user.fname }} {{ this.user.lname }}</p>
      <p>Email: {{this.user.email}}</p>
      <p>Password: {{this.user.password}}</p>
      <div class="buttons">
        <button class="mainbtn button" type="button" v-on:click.prevent="signOut">Sign Out</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RegForm',
  data: function () {
    return {
      user: {
        fname: '',
        lname: '',
        email: '',
        password: '',
        passwordConfirm: ''
      },
      showForm: true,
      showReceipt: false,
      showErrorMessage: false,
      errorMessage: ''
    }
  },

  methods: {
    /**
     * @function submitForm()
     * If input is valid, this method hides the registration form
     * and reveals the successful registration receipt
     */
    submitForm: function () {
      // Check that password had been correctly confirmed
      if (this.user.password !== this.user.passwordConfirm) {
        return
      }
      // show success receipt and hide registration form
      this.showReceipt = true
      this.showForm = false
    },

    /**
     * @function clearForm()
     * Empties and resets the registration form
     */
    clearForm: function () {
      // Resets all input fields and exception messages to default/empty
      this.user.fname = ''
      this.user.lname = ''
      this.user.email = ''
      this.user.password = ''
      this.user.passwordConfirm = ''
      this.showErrorMessage = false
    },

    /**
     * @function checkPassword()
     * This method checks the password and confirmPassword props,
     * and displays a message indicating whether or not they match
     */
    checkPassword: function () {
      this.showErrorMessage = true
      // Verify that "password" user input matches "password confirm" input
      // Happy path
      if (this.user.password === this.user.passwordConfirm) {
        this.errorMessage = 'Password match'
        document.getElementById('errorMessage').style.color = 'green'
      } else {
        this.errorMessage = 'Password does not match'
        document.getElementById('errorMessage').style.color = 'red'
      }
    },

    /**
     * @function signOut()
     * This function is a duct-tape fix to simulate the user signing out.
     * Reloads the page, which resets data and shows and hides different elements
     */
    signOut: function () {
      // Reload page to simulate signing out
      location.reload()
    }
  }
}
</script>

<style lang="scss" scoped>
$main-color: #225773;
$accent-color: #bf5543;
$bg-color: #eaeaea;

.form {
  margin: auto;
  width: 40%;
  padding: 10px;
  border: 1px solid $main-color;
  border-radius: 12px;
  background-color: $bg-color;
  text-align: left;
  h1, h2, .buttons {
    text-align: center;
  }
}

input[type=text], input[type=email], input[type=password], select {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
}

.button {
  background-color: white;
  border: 2px solid $accent-color;
  color: $main-color;

  border-radius: 8px;
  padding: 16px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
  &:hover {
    background-color: $main-color;
    color: white;
  }
}

.mainbtn {
  background-color: $main-color;
  border: 2px solid $accent-color;
  color: white;
  &:hover {
    background-color: white;
    color: $main-color;
  }
}

label, p, .button{
  font-weight: bold;
}

#fname, #lname {
  text-transform: capitalize;
}

/* Responsive form width, gets larger for mobile screens */
@media (max-width: 600px) {
  .form {
    width: 90%;
  }
}
</style>
