<template>
  <div>
    <form @submit.prevent="userLogin">
      <div>
        <label>Email</label>
        <input type="email" v-model="email" />
      </div>
      <div>
        <label>Password</label>
        <input type="text" v-model="password" />
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {

    data() {
      return {
        email: '',
        password: ''
      }
    },
    methods: {
      async userLogin() {
        /*await this.$axios.get('/sanctum/csrf-cookie', {
          headers: {
            'X-Requested-With': 'XMLHttpRequest'
          },
          credential: true,
        }).then(response => {
          console.log(response);
        })*/

        await this.$auth.loginWith('laravelSanctum', {
          data: {
            email: this.email,
            password: this.password
          }
        })
      }
    }
  }
</script>
