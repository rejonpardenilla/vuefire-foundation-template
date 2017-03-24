<template>
  <div id="login">

    <div class="row align-center text-center">
      <div class="column small-10 medium-8 large-6">
        <a class="button expanded" @click="facebookLogin">Login with Facebook</a>
      </div>
    </div>

    <div class="row align-center text-center">
      <div class="column small-10 medium-8 large-6">
        <a class="button expanded" @click="googleLogin">Login with Google</a>
      </div>
    </div>

  </div>
</template>

<script>

  import Firebase from 'firebase'
  import firebase from '../firebase'
  var auth = firebase.auth()

  export default {

    name: 'login',

    methods: {
      facebookLogin () {
        let provider = new Firebase.auth.FacebookAuthProvider()

        auth.signInWithPopup(provider)
      },

      googleLogin () {
        let provider = new Firebase.auth.GoogleAuthProvider()

        auth.signInWithPopup(provider)
      }

    },

    beforeCreate () {
      auth.onAuthStateChanged(function (user) {
        if (user) this.$router.replace('/')
      }.bind(this))
    }

  }
</script>

<style scoped>
  #login {
    padding-top: 5em;
  }
</style>
