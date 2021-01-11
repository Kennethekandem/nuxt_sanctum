<template>
  <div>
    <form @submit.prevent="userLogin">
      <div>
        <label>Username</label>
        <input type="text" v-model="login.username" />
      </div>
      <div>
        <label>Password</label>
        <input type="text" v-model="login.password" />
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'login',

    data() {
      return {
        login: {
          username: '',
          password: ''
        }
      }
    },
    methods: {
      async userLogin() {
        await this.$axios.get('/sanctum/csrf-cookie', {
          headers: {
            'X-Requested-With': 'XMLHttpRequest'
          },
          withCredentials: true,
        }).then(response => {
          console.log(response);
        })
      }
    }
  }
</script>
