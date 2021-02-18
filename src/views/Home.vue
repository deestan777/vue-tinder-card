<template>
  <div class="start">
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <GameCardStack />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import GameCardStack from "@/components/GameCardStack";

export default {
  name: "Home",
  components: {
    HelloWorld,
    GameCardStack
  }
};
</script>

<style lang="less" scoped>
.start {
  background: #000;
}
</style>
