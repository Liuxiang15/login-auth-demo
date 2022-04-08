<template>
  <h1>正在登录中...</h1>
</template>

<script>
export default {
  created() {
    // this.unWatch = this.$store.watch( // 两种写法都可以，一个是vue的，一个是vuex的
      this.unWatch = this.$watch(
      () => this.$store.getters["loginUser/status"],
      (status) => {
        if (status !== "loading") {
          this.$router
            .push(this.$route.query.returnurl || "/home")
            .catch(( ) => {});
        }
      },
      {
        immediate: true,
      }
    );
  },
  destroyed() {
    this.unWatch();
  },
};
</script>

<style></style>
