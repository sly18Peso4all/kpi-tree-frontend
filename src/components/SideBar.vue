<template>
  <div class="navigation">
    <h5 class="heading">Navigation</h5>

    <ul id="example-1">
      <li v-for="item in items" :key="item.message">
        &#11201; {{ item.message }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SideBar",

  data() {
    return {
      items: [
        { message: "My Dashboard", icon: "&#11201;" },
        { message: "planning", icon: "&#11201;" },
        { message: "Reporting", icon: "&#11201;" },
        { message: "Execution", icon: "&#11201;" },
        { message: "Data Input", icon: "&#11201;" },
      ],
    };
  },
};
</script>

<style scoped>
.navigation {
  background: #404040;
  width: 15%;
  height: 100vh;
}

.heading {
  margin-top: 1rem;
  margin-left: 0.5rem;
}

ul {
  display: flex;
  flex-direction: column;
  list-style: none;
  margin-top: 2rem;
  cursor: pointer;
}

ul li {
  display: block;

  height: 100%;
  width: 100%;
  line-height: 20px;
  padding: 0.5rem;
  color: orange;

  padding-left: 10px;
  transition: 0.5s;
  font-size: 14px;
}

ul li:hover {
  padding-left: 20px;
}
</style>
