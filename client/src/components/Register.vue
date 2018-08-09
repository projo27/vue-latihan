<template>
  <div>
   <h1>Register</h1>
   <input type="email" name="email" placeholder="email" v-model="email" /><br />
   <input type="password" name="password" placeholder="password" v-model="password"><br />
   <button @click="register">Register</button>
  </div>
</template>

<script>
import AuthenticationService from '../../services/AuthenticationService'
export default {
  name: "Register",
  data() {
    return {
      email: "email",
      password: "password"
    };
  },
  watch: {
    email (value) {
      console.log("email berubah", value)
    }
  },
  mounted() {
    setTimeout(() => {
      this.email = "hello world";
    }, 2000);
  },
  methods: {
    async register (){
      const response = await AuthenticationService.register({
        email: this.email,
        password: this.password
      })
      console.log(response.data)
    }
    // register() {
    //   console.log("tombol register telah terpilih", this.email, this.password);
    // }
  }
};
</script>


<style scoped>
</style>
