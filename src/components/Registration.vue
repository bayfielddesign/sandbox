<template>
  <!--container div for whole document-->
  <div class="container">

    <!--We are making a registartion form. Lets start with the basic html-->
    <!--We need a tile followed by 5 input fields and 2 buttons-->
    <!--We also need a text box to display a confirmation message and receipt-->
    <div class="colomn">

    <header>
      <h1>{{msg}}</h1>
    </header>

    <div class="colomn-content">
    <!--This form should display as a coloumn and contain instrictions, input fields and buttons-->
    <form @submit.prevent="submitForm" autocomplete="off" name="register">
      <table cellspacing="0" cellpadding="0" border="0">
        <tbody>
          <!--Heading and instructions-->
          <tr class="tableHeading">
            <td colspan="2">Instructions</td>
          </tr>
          <tr>
            <td class="instructions" colspan="2"><strong>Welcome!</strong> Please fill out the fields to complete your registartion.</td>
          </tr>
          <tr class="tableHeading">
            <td colspan="2">Information</td>
          </tr>
          <!--Input fields-->
          <!--Not sure if ":" should be inside the label tags for accessibility purposes-->
          <tr>
            <td>
              <label for="firstname">First Name:</label>
            </td>
            <td>
              <input v-model="form.firstName" type="text" id="firstname"/>
              <p v-if="!firstNameIsValid" class="error-message">First name is required</p>
            </td>
          </tr>
          <tr>
            <td>
              <label for="lastname">Last Name:</label>
            </td>
            <td>
              <input v-model="form.lastName" type="text" id="lastname"/>
              <p v-if="!lastNameIsValid" class="error-message">Last name is required</p>
            </td>
          </tr>
          <tr>
            <td>
        <label for="email">Email:</label>
            </td>
            <td>
        <input v-model="form.email" type="email" id="email"/>
        <p v-if="!emailIsValid" class="error-message">Email is required</p>
            </td>
          </tr>
          <tr>
            <td>
        <label for="password">Password:</label>
            </td>
            <td>
        <input v-model="form.password" type="password" id="password"/>
        <p v-if="!passwordIsValid" class="error-message">Password is required</p>
            </td>
          </tr>
          <tr>
            <td>
        <label for="confirmpassword">Confirm Password:</label>
            </td>
            <td>
        <input v-model="form.confirmPassword" type="password" id="confirmpassword"/>
        <p v-if="!confirmPasswordIsValid" class="error-message">Must match password</p>
            </td>
          </tr>
        <!--Buttons-->
        <tr>
          <td class="buttonRow" colspan="2">
            <button type="reset" role="button" @click="handleClick">Reset</button>
            <button :disabled="!formIsValid" type="submit" role="button">Submit</button>
          </td>
        </tr>
        </tbody>
      </table>
    </form>
    <!--Hidden element to display confirmation and receipt-->
    <div v-show="show" class="hidden-confirmation">
      <h2 class="confirmHeader">Confirmation - Success!</h2>
      <p>First Name: {{ this.form.firstName }}</p>
      <p>Last Name: {{ this.form.lastName }}</p>
      <p>Email: {{ this.form.email }}</p>
      <p>Password: {{ this.form.password }}</p>
    </div>
    </div>
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
      // form valadation fields
      show: false,
      form: {
        firstName: null,
        lastName: null,
        email: null,
        password: null,
        confirmPassword: null
      }
    }
  },

  computed: {
    // validating fields
    firstNameIsValid () {
      return !!this.form.firstName
    },

    lastNameIsValid () {
      return !!this.form.lastName
    },

    emailIsValid () {
      return !!this.form.email
    },

    passwordIsValid () {
      return !!this.form.password
    },
    // TODO: add some more requirments like uppercase, lowercase, numbers to password
    confirmPasswordIsValid () {
      return !!this.form.confirmPassword && this.form.confirmPassword === this.form.password
    },

    formIsValid () {
      return this.firstNameIsValid && this.lastNameIsValid && this.emailIsValid && this.passwordIsValid && this.confirmPasswordIsValid
    }
  },

  methods: {
    // checking form validation
    submitForm () {
      if (this.formIsValid) {
        console.log('Valid')
        console.log(this.show)
        this.show = true
        return true
      } else {
        return false
      }
    },
    // Reset fields and hide confirmation box
    handleClick: function () {
      this.show = false
      this.form.firstName = null
      this.form.lastName = null
      this.form.email = null
      this.form.password = null
      this.form.confirmPassword = null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
//TODO add support for different devices, still doesn't look terrible on small screen
.container{
  //color: #fff;
  //background-color: #5995DA;  /* Blue */
  padding: 10px 10px;
  display: flex;
  justify-content: center;
}
.colomn{
  width: 700px;
  //background-color: rgb(226, 226, 226);
  border-style: solid;
  border-width: 1px;
}
.colomn-content{
  padding-top: 10px;
}
form{
  padding-bottom: 10px;
}
table{
  margin-left: auto;
  margin-right: auto;
  border: black;
  border-style: solid;
  border-width: 1px;
}
tr{
  padding-top: 5px;
}
tr:nth-child(even) {
  background-color: #f2f2f2;
}
td{
  text-align: left;
  padding: 10px;
}
//TODO: Make better color palette so heading are more readable
.tableHeading td{
  font-size: 150%;
  padding-top: 10px;
  padding-bottom: 10px;
  text-align: left;
  background-color: #D6E9FE;
  color: white;
}
//This should probably refer to a class of td instead of all labels
label{
  padding-right: 100px;
}
.buttonRow{
  text-align: center;
}
button{
  margin-left: 10px;
  margin-right: 10px;
  width: 15%;
}

.instructions{
  padding-top: 10px;
  padding-bottom: 10px;
}
header{
  background-color: #005776;
  color: white;
  border: black;
  border-style: solid;
  border-bottom-width: 1px;
  border-top-width: 0px;
  border-left-width: 0px;
  border-right-width: 0px;
}
//TODO: make this look more polished
.hidden-confirmation{
  border: black;
  border-style: solid;
  border-width: 1px;
  text-align: left;
  margin-left: auto;
  margin-right: auto;
  width: 300px;
  padding: 10px;
}
.confirmHeader{
  text-align: center;
}
/*button
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
*/
</style>
