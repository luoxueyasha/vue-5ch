<template>

  <div id="app">
    <p style="height:50px"></p>
    <THREADCONTENTS />
    <p style="height:50px"></p>
  </div>

</template>

<script>
import THREADCONTENTS from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    THREADCONTENTS,
  },
};

</script>

<style>
#app {
  font-family: Saitamaar, "MS Gothic", Simsun;
  margin: 0;
  padding: 0;
  color: #000000;
  background: #ffffff;
  background-repeat: repeat;
  background-attachment: fixed;
  font-weight: 600;
}
</style>
