<template>
<main>
    <h2>SignIn</h2>
    <form @submit.prevent>
        <input type="text" v-model="username" placeholder="Username" required />
        <input type="password" v-model="password" placeholder="Password" required />
        <div v-if="erroData != null">{{errorData}}</div>
        <button @click="submitData()">
            Login <span v-if="isLoading">loading ....</span>
        </button>
    </form>
    <p> <a href="#">forgot password?</a> <a href="#">Already have account?</a></p>
</main>
</template>

<script>
export default {
    name : 'LoginPage',
    data() {
        return {
            username : '',
            password : '',
            isLoading : false,
            errorData : null
        }
    },
    methods: {
        submitData() {
            this.isLoading = true
            setTimeout(() => {
                if (this.username ==  '' || this.password == '') {
                    this.errorData = "All fields are required"
                    this.isLoading = false
                }else {
                    localStorage.setItem("username", this.username)
                    this.$router.push('/dashboard')
                    this.errorData = null
                    this.isLoading = false
                }
            }, 1000);

        }
    },
}
</script>

<style scoped>
    input {
        display: block;
        margin: 1rem 0;
        padding: 0.5rem;
        width: 100%;

    }
    button {
        padding: 0.5rem 1rem;
    }

  h2{
    text-align: left;
    width: 15vw;
  }
  form {
      border: 1px solid;
        width: 90%;
        padding: 1rem;
        margin: 0 auto;

  }
  main {
        width: 100%;
        background: linear-gradient(to left, rgba(0, 0, 0, 0.5 ), rgba(0, 0, 0, 0.8));

  }

  @media only screen and (min-width: 768px) {
      form {
      width: 40%;
  }
  }

</style>