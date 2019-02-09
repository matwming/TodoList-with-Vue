<template>
  <div id="app">
    <div id="nav">
      <Header/>
    </div>
    <router-view/>
  </div>
</template>
<script>
import Header from "./components/layout/Header";
export default {
  name: "app",
  components: {
    Header
  }
};
</script>

<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  margin: 5px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
</style>
