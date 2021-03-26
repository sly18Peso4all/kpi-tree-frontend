<template>
  <div class="main-dashboard">
    <h4>Operational Dashboard</h4>

    <h5>{{ title }}</h5>
    <NodeTree v-bind:node="tree" class="kpi" />
  </div>
</template>

<script>
import NodeTree from "./NodeTree";
import axios from "axios";

export default {
  name: "tree",
  props: {
    title: String,
  },
  components: {
    NodeTree,
  },
  data() {
    return {
      tree: {},
    };
  },
  mounted() {
    axios
      .get("http://localhost:5000/")
      .then((response) => {
        // console.log(response.data);
        this.tree = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
.kpi {
  margin-top: 6rem;
  margin-left: 1rem;
  width: 100%;
}

h4 {
  margin-top: 2rem;
  margin-left: 1rem;
}

h5 {
  margin-top: 3rem;
  color: orange;
  margin-left: 2rem;
}
</style>
