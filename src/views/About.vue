<template>
  <div class="about">
    <h1>התחברות</h1>
    <input placeholder="שם" type="text">
    <div id="nav">
      <button @click="onChatClick">התחבר</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'About',
    methods: {
      onChatClick() {
        this.$router.push("/chat")
      }
    },
  }
</script>
