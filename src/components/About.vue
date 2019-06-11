<template>
  <div>
    <p>Hello {{their_name}}</p>
  </div>
</template>

<script>
export default {
  name: "About",
  data() {
    return {
      their_name: this.$route.params.name
    };
  }
};
</script>

<style>
</style>
