<template>
  <div id="app">
    <SideBar />
    <KpiTree title="Value Tree" />
  </div>
</template>

<script>
import KpiTree from "./components/KpiTree";
import SideBar from "./components/SideBar";

export default {
  name: "App",
  components: {
    SideBar,
    KpiTree,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Roboto+Condensed");
@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500&display=swap");

* {
  margin: 0;
  border: 0;
  box-sizing: border-box;
}
#app {
  font-family: "Roboto", sans-serif;

  display: flex;
}

body {
  background: #121212;
  height: 100vh;
  color: #f1f1f1;
  font-family: "Roboto", sans-serif;
}
</style>
