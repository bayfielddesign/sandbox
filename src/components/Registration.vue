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
    <form name="register">
      <table cellspacing="0" cellpadding="0" border="0">
        <tbody>
          <!--Heading and instructions-->
          <tr class="tableHeading">
            <td colspan="2">Instructions</td>
          </tr>
          <tr>
            <td class="instructions" colspan="2"><strong>Welcome!</strong> Please fill out the fields below to complete your registartion.</td>
          </tr>
          <tr class="tableHeading">
            <td colspan="2">Information</td>
          </tr>
          <!--Input fields-->
          <tr>
            <td>
              <label for="firstname">First Name: </label>
            </td>
            <td>
              <input type="text" id="firstname"/>
            </td>
          </tr>
          <tr>
            <td>
              <label for="lastname">Last Name: </label>
            </td>
            <td>
              <input type="text" id="lastname"/>
            </td>
          </tr>
          <tr>
            <td>
        <label for="email">Email: </label>
            </td>
            <td>
        <input type="email" id="email"/>
            </td>
          </tr>
          <tr>
            <td>
        <label for="password">Password: </label>
            </td>
            <td>
        <input type="password" id="password"/>
            </td>
          </tr>
          <tr>
            <td>
        <label for="confirmpassword">Confirm Password: </label>
            </td>
            <td>
        <input type="password" id="confirmpassword"/>
            </td>
          </tr>
        <!--Buttons-->
        <tr>
          <td class="buttonRow" colspan="2">
            <button type="reset">Reset</button>
            <button type="submit">Submit</button>
          </td>
        </tr>
        </tbody>
      </table>
    </form>
    <!--Hidden element to display confirmation and receipt-->
    <div v-if="true" class="hidden-conformation">confirmation and receipt</div>
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
    }
  },
  methods: {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
//TODO add support for different devices
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
//TODO: Make better color palate so heading are more readable
.tableHeading td{
  font-size: 150%;
  padding-top: 10px;
  padding-bottom: 10px;
  text-align: left;
  background-color: #D6E9FE;
  color: white;
}
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
