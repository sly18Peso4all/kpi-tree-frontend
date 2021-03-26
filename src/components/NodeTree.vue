<template>
  <li class="tree">
    <div class="header" @click="expand">
      <h5>
        <span>{{ node.name }}</span>
        <span class="toggle" v-if="isNode">{{
          expanded ? "&#5123;" : "&#5121;"
        }}</span>
      </h5>

      <div class="tree-details">
        <div>
          <span v-bind:class="applyStyle()">{{ node.value.amount }}</span>
        </div>
        <div>
          <span v-bind:class="applyArrow()">{{
            node.delta.color == "red" ? "&#9660;" : "&#9650;"
          }}</span>
          <span>{{ node.delta.amount }}</span>
        </div>
      </div>
    </div>
    <ul v-show="expanded" v-if="isNode">
      <node
        v-for="(child, index) in node.children"
        :key="index"
        :node="child"
      ></node>
    </ul>
  </li>
</template>

<script>
export default {
  name: "node",
  props: {
    node: Object,
  },
  data() {
    return {
      expanded: false,
    };
  },
  computed: {
    isNode() {
      return this.node.children && this.node.children.length;
    },
  },
  methods: {
    expand() {
      if (this.isNode) {
        return (this.expanded = !this.expanded);
      }
    },
    applyStyle() {
      if (this.node.value.color == "red") return "red";
      if (this.node.value.color == "orange") return "orange";
      if (this.node.value.color == "green") return "green";
    },
    applyArrow() {
      if (this.node.delta.color == "red") return "red-arrow";
      if (this.node.delta.color == "orange") return "orange-arrow";
      if (this.node.delta.color == "green") return "green-arrow";
    },
  },
};
</script>

<style scoped>
.tree {
  list-style-type: none;
  transition: 0.5s;
}

h5 .toggle {
  margin-left: 1rem;
  color: orange;
  font-size: 15px;
  transition: all 0.6s;
}

.tree ul {
  padding-top: 20px;
  position: relative;

  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
  list-style-type: none;
}

.tree li {
  float: left;
  text-align: center;
  list-style-type: none;
  position: relative;
  padding: 20px 5px 0 5px;

  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

.tree li::before,
.tree li::after {
  content: "";
  position: absolute;
  top: 0;
  right: 50%;
  border-top: 1px solid orange;
  width: 50%;
  height: 20px;
  z-index: 1;
}

.tree li::after {
  right: auto;
  left: 50%;
  border-left: 1px solid orange;
}

.tree li:only-child::after,
.tree li:only-child::before {
  display: none;
}

.tree li:only-child {
  padding-top: 0;
}

.tree li:first-child::before,
.tree li:last-child::after {
  border: 0 none;
}

.tree li:last-child::before {
  border-right: 1px solid orange;
  border-radius: 0 5px 0 0;
  -webkit-border-radius: 0 5px 0 0;
  -moz-border-radius: 0 5px 0 0;
}
.tree li:first-child::after {
  border-radius: 5px 0 0 0;
  -webkit-border-radius: 5px 0 0 0;
  -moz-border-radius: 5px 0 0 0;
}

.tree ul ul::before {
  content: "";
  position: absolute;
  top: 0;
  left: 50%;
  border-left: 1px solid orange;
  width: 0;
  height: 20px;
}

.tree li a {
  border: 1px solid #ccc;
  padding: 5px 10px;
  text-decoration: none;
  color: #666;
  font-family: arial, verdana, tahoma;
  font-size: 11px;
  display: inline-block;
  border-radius: 5px;
  -webkit-border-radius: 5px;
  -moz-border-radius: 5px;
  transition: all 0.5s;
  -webkit-transition: all 0.5s;
  -moz-transition: all 0.5s;
}

h5 {
  border: 1px solid transparent;
  background: #404040;

  width: 15%;
  margin: 0 auto;
  padding: 10px;
  min-width: 150px;
  display: flex;
  justify-content: space-between;
  transition: all 0.6s;
}

.header .tree-details {
  display: flex;
  width: 15%;
  text-align: center;
  margin: 0 auto;
  border: 1px solid transparent;
  padding: 10px;
  justify-content: space-around;
  min-width: 150px;
  position: relative;
  background: rgba(14, 14, 87, 0.058);
  border-top-color: #f1f1f1;
  font-size: 10px;
  background: #404040;
}

.header {
  margin: 0 auto;
  text-align: center;
  position: relative;
  cursor: pointer;
}

.tree ul > * > * > * {
  min-width: 150px;
  padding: 10px;

  list-style-type: none;
  position: relative;
  z-index: 100;
  transition: all 0.6s;
}

.orange,
.orange-arrow {
  color: orange;
}

.red,
.red-arrow {
  color: red;
}

.green,
.green-arrow {
  color: green;
}
</style>
