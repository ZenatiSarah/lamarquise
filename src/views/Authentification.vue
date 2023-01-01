<template>
  <div class="auth">
    <img src="../assets/logo_lamarquise.jpg" />

    <form @submit="checkForm" method="post">
      <p v-if="this.mode === 'login'">
        Tu n'as pas encore de compte ?
        <span class="card__action" @click="switchToSignup()"
          >Créer un compte</span
        >
      </p>
      <p v-if="this.mode === 'signup'">Tu as déjà un compte ?</p>
      <p>
        <label for="email">Email</label>
        <input id="email" model="email" type="email" name="email" />
      </p>
      <p>
        <label for="password">Password</label>
        <input id="password" model="password" type="text" name="password" />
      </p>

      <p>
        <input type="submit" value="Submit" />
      </p>
    </form>
  </div>
</template>

<script>
export default {
  name: "authLogin",
  data: function () {
    return {
      mode: "login",
      email: "",
      password: "",
    };
  },
  methods: {
    switchToSignup() {
      this.mode = "signup";
    },
    switchToLogin() {
      this.mode = "login";
    },
    checkForm(e) {
      e.preventDefault();
      this.errors = [];

      if (this.email === null) {
        this.errors.push("Veuillez entrer un email");
      } else {
        console.log(this.email + "mail correct");
      }
    },
  },
};
</script>


<style scoped>
.auth {
  align-items: center;
  display: flex;
  flex-direction: column;
}
form {
  border: 1px solid;
  border-radius: 15px;
  width: 25rem;
  height: 18rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 5rem;
}

p {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
</style>