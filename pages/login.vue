<template>
  <section id="login">
    <div class="login container">
      <div class="row login-row">
        <div class="col l24 login-col">
          <div v-if="isLogin==true" class="login-texts flex flex-column">
            <h2 class="white-text">Admin Login</h2>

            <div class="form-group">
              <label class="control-label">
                Email
                <span class="symbol required"></span>
              </label>
              <span class="input-icon">
                <input
                  id="email"
                  type="email"
                  class="form-control"
                  maxlength="50"
                  placeholder="Email"
                  ng-model="email"
                >
                <i class="fa fa-envelope"></i>
              </span>
            </div>
            <div
              class="form-group"
              ng-class="{'has-error':Form.password.$dirty && Form.password.$invalid, 'has-success':Form.password.$valid}"
            >
              <label class="control-label">
                Password
                <span class="symbol required"></span>
              </label>
              <span class="input-icon">
                <input
                  id="password"
                  type="password"
                  class="form-control"
                  maxlength="25"
                  placeholder="Password"
                  ng-model="password"
                >
                <i class="fa fa-lock"></i>
              </span>
            </div>

            <div class="row">
              <div class="col l12">
                <!-- <button
                  type="submit"
                  class="btn white-text loginButton"
                  style="border: 1px solid grey"
                >Join</button> -->
              </div>

              <div class="col l24">
                <button
                  @click="login"
                  type="submit"
                  class="btn btn-my-blue white-text loginButton"
                >Login</button>
              </div>

              <div class="col l24">
                <p style="color:white;cursor:pointer" @click="changeMode(false)">Change Password</p>
              </div>



            </div>
          </div>
          <div v-if="isLogin==false" class="login-texts flex flex-column">
            <h2 class="white-text">Pass Login</h2>
            <p id="error"></p>
            <div class="form-group">
              <label class="control-label">
                Email
                <span class="symbol required"></span>
              </label>
              <span class="input-icon">
                <input
                  id="change_email"
                  type="email"
                  class="form-control"
                  maxlength="50"
                  placeholder="Email"
                  ng-model="email"
                >
                <i class="fa fa-envelope"></i>
              </span>
            </div>

            <div class="form-group">
              <label class="control-label">
                Old password
                <span class="symbol required"></span>
              </label>
              <span class="input-icon">
                <input
                  id="change_old_p"
                  type="password"
                  class="form-control"
                  maxlength="50"
                  placeholder="Email"
                  ng-model="email"
                >
                <i class="fa fa-envelope"></i>
              </span>
            </div>
            <div
              class="form-group"
              ng-class="{'has-error':Form.password.$dirty && Form.password.$invalid, 'has-success':Form.password.$valid}"
            >
              <label class="control-label">
                New Password
                <span class="symbol required"></span>
              </label>
              <span class="input-icon">
                <input
                  id="change_new_p"
                  type="password"
                  class="form-control"
                  maxlength="25"
                  placeholder="Password"
                  ng-model="password"
                >
                <i class="fa fa-lock"></i>
              </span>
            </div>

            <div class="row">
              <div class="col l12">
                <!-- <button
                  type="submit"
                  class="btn white-text loginButton"
                  style="border: 1px solid grey"
                >Join</button> -->
              </div>

              <div class="col l24">
                <button
                  @click="changePass"
                  type="submit"
                  class="btn btn-my-blue white-text loginButton"
                >Change Password</button>
              </div>

              <div class="col l24">
                              <p style="color:white;cursor:pointer" @click="changeMode(true)">Go to Login</p>
              </div>



            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>


<style scoped>
#login {
  background-image: url('~static/logo.png');
  background-size: cover;
  width: 100%;
  height: 100%;
}

.login-row {
  height: 390px;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto 15%;
  max-width: 300px;
  border-radius: 5px;
  box-shadow: 1px 4px 19px 7px rgba(0, 0, 0, 0.18);
}

.loginButton {
  width: 100px;
}

.backgroundcolor {
  background-color: white;
  border-radius: 5px 0 0 5px;
}

.control-label {
  color: white;
}

.login-texts {
  height: 100%;
  padding: 0 5px;
}

.login-col {
  padding-left: 40px;
  padding-right: 40px;
  padding-top: 20px;
  background-color: #0d164b;
  height: 100%;
  border-radius: 5px;
}

.underline {
  line-height: 1;
  position: relative;
  display: block;
  margin: 1em 0;
  font-weight: bold;
  line-height: 1.4;
  padding-bottom: 10px;
}

.underline::before {
  background-color: white;
  content: '';
  position: absolute;
  z-index: 1;
  color: red;
  bottom: 0;
  left: 0;
  width: 35%;
  height: 5px;
  opacity: 1;
  border-radius: 10px;
}

.white-text{
    color: white
}

input[type="password"], input[type="email"]{
    outline: 0;
    border: 1px solid #e8e8e8;
    padding: 10px;
    border-radius: 2px;
    width: 100%;
}

.control-label{
    display: flex;
}


@media screen and (min-width: 1199px) {
  .login-row{
    margin: auto;
  }
}

.btn{
    text-decoration: none;
    color: #fff;
    background-color: #f37638;
    text-align: center;
    letter-spacing: .5px;
    transition: background-color .2s ease-out;
    cursor: pointer;
    margin: 10px 0;
    border: none;
    border-radius: 2px;
    display: inline-block;
    height: 36px;
    line-height: 36px;
    padding: 0 16px;
    text-transform: uppercase;
    width: 100%;
    vertical-align: middle;
    -webkit-tap-highlight-color: transparent;
}



</style>


<script>
import axios from 'axios'
axios.defaults.withCredentials = true

export default {
  name: 'login',
  data() {
    return {
      jokes: [],
      loading: false,
      isLogin: true
    }
  },
  methods: {
    changeMode: function(e) {

        this.isLogin = e



    },
    login: function() {


      var bodyFormData = new FormData()

      bodyFormData.append('email', document.getElementById('email').value)
      bodyFormData.append('password', document.getElementById('password').value)

      axios({
        method: 'POST',
        url: "https://www.cheapairhub.com/api/api.php?login=login",
        headers: {
          'Content-Type': 'multipart/form-data'
        },
        data: bodyFormData
      })
        .then(res => {
          console.log('res', res.data)

          if(res.data.code == 200){

            localStorage.setItem('random' , res.data.token)

              this.$router.push('/admin')
          }


          
        })
        .catch(err => {
          console.log('error in request1', err.response.data.message)
        })
    },
    changePass: function() {


      var bodyFormData = new FormData()

      bodyFormData.append('email', document.getElementById('change_email').value)
      bodyFormData.append('old_password', document.getElementById('change_old_p').value)
      bodyFormData.append('new_password', document.getElementById('change_new_p').value)

      axios({
        method: 'POST',
        url: "https://www.cheapairhub.com/api/api.php?changePass=changePass",
        headers: {
          'Content-Type': 'multipart/form-data'
        },
        data: bodyFormData
      })
        .then(res => {
          console.log('res', res.data)

          if(res.data.code == 200){

            $("input").val("")

            $("#error").html("Successfully Changed")
            $("#error").removeClass("hide")
            

            this.isLogin = true

          }else{

            $("#error").html("Error on change")
            $("#error").removeClass("hide")

          }


          // this.$router.push('/admin')
        })
        .catch(err => {
          console.log('error in request1', err.response.data.message)
        })
    }
  }
}
</script>
