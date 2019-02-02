<template lang="pug">
  div
    h1 User profile for
    h3 {{this.$route.params.user_id}}
</template>

<script>
export default {
  watch: {
    '$route': (to, from) => {
      console.log('USER PROFILE:');
      console.log(to);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
