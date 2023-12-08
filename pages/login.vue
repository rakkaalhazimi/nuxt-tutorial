<script setup lang="ts">
  const isLogin = ref(false);
  const inputUsername = ref('');
  const inputPassword = ref('');

  const user = reactive({
    isLogin: false,
    username: '',
  })

  function login() {
    if (
      inputUsername.value.length > 0 &&
      inputPassword.value.length > 0
    ) {
      user.username = inputUsername.value;
      isLogin.value = true;
    }
  }

  function logout() {
    isLogin.value = false;
  }
</script>

<template>
  <section v-if="!isLogin">
    <form action="">
      <div>
        <label for="input-username">Username: </label>
        <input type="text" id="input-username" v-model="inputUsername" />
      </div>
      <div>
        <label for="input-password">Password: </label>
        <input type="password" id="input-password" />
      </div>
      <input type="submit" value="Login" @click.prevent="login" />
    </form>

    <div>You have logged out</div>
  </section>


  <section v-else>
    <p>You have logged in</p>
    <p>Welcome {{ user.username }}</p>
    <button @click="logout">Logout</button>
  </section>
</template>