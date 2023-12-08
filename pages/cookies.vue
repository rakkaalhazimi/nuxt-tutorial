<script setup lang="ts">
  const key = ref('');
  const value = ref('');
  const keyFind = ref('');
  const valueFound = ref('');

  function saveCookie() {
    if (key.value.length > 0 && value.value.length > 0) {
      const cookie = useCookie(key.value, {maxAge: 60});
      cookie.value = value.value;
      
      key.value = '';
      value.value = '';
    }
  }

  function findCookie() {
    const cookie = useCookie(keyFind.value);
    valueFound.value = cookie.value || '';
  }
</script>

<template>

  <h1>Cookies</h1>
  <p>Enter key and value for cookie, then check it in your browser</p>

  <form>
    <div>
      <label for="cookie-key">Key: </label>
      <input type="text" id="cookie-key" v-model="key" />
    </div>
    <div>
      <label for="cookie-value">Value: </label>
      <input type="text" id="cookie-value" v-model="value" />
    </div>
    <input type="submit" value="create" @click.prevent="saveCookie" />
  </form>

  <div>
    <p>Check your cookies</p>
    <input type="text" id="cookie-search" v-model="keyFind">
    <button @click="findCookie">Search</button>
    
    <p>Found: {{ valueFound }}</p>
    
  </div>

</template>