<template>
  <div id="LoginForm">
    <div class="container">
        <div class="login-form">
                  <h1 class="header">Login</h1>
            <div class="main-div">
                <div class="panel">
                </div>
                 <form id="Login">
                    <div class="form-group">
                        <input type="email" class="form-control" id="inputEmail" placeholder="Email Address" v-model="email">
                    </div>
                     <div class="form-group">
                        <input type="password" class="form-control" id="inputPassword" placeholder="Password" v-model="password" @keydown.enter="login">
                    </div>
                    <button type="submit" class="btn btn-primary" @click="login">Login</button>
                    <p>Didn't have account yet ?</p>
                    <p><router-link to="/signup">create an account</router-link></p>
                </form>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
import firebase from 'firebase';

export default {
  name: "login",
  data: function() {
    return {
        email:"",
        password:"",
    }
  },
  methods:{
      login:function(e){
          firebase.auth().signInWithEmailAndPassword(this.email,this.password)
            .then(user=>{
                this.$router.push('/')
            },err=>{
                alert(err.message)
            })

        e.preventDefault()
      }
  }
};
</script>

<style>
div#LoginForm{ background-image:url("https://hdwallsource.com/img/2014/9/blur-26347-27038-hd-wallpapers.jpg"); background-repeat:no-repeat; background-position:center; background-size:cover; padding:10px;}

.header{color:white}
.form-heading { color:#fff; font-size:23px;}
.panel h2{ color:#444444; font-size:18px; margin:0 0 8px 0;}
.panel p { color:#777777; font-size:14px; margin-bottom:30px; line-height:24px;}
.login-form .form-control {
  background: #f7f7f7 none repeat scroll 0 0;
  border: 1px solid #d4d4d4;
  border-radius: 4px;
  font-size: 14px;
  height: 50px;
  line-height: 50px;
}
.main-div {
  background: #ffffff none repeat scroll 0 0;
  border-radius: 2px;
  margin: 10px auto 30px;
  max-width: 40%;
  padding: 50px 70px 70px 71px;
}

.login-form .form-group {
  margin-bottom:10px;
}
.login-form{ text-align:center;}
.forgot a {
  color: #777777;
  font-size: 14px;
  text-decoration: underline;
}
.login-form  .btn.btn-primary {
  background: #f0ad4e none repeat scroll 0 0;
  border-color: #f0ad4e;
  color: #ffffff;
  font-size: 14px;
  width: 100%;
  height: 50px;
  line-height: 50px;
  padding: 0;
}
.forgot {
  text-align: left; margin-bottom:30px;
}
.botto-text {
  color: #ffffff;
  font-size: 14px;
  margin: auto;
}
.login-form .btn.btn-primary.reset {
  background: #ff9900 none repeat scroll 0 0;
}
.back { text-align: left; margin-top:10px;}
.back a {color: #444444; font-size: 13px;text-decoration: none;}

</style>
