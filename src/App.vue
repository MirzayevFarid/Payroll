
<template>
  <div id="app">
    <div id="TopBar">
      <h2 id="text" class="d-inline-block text-right">
        Focus on your product,
        <br />not your
        <span class="payroll-ls">payroll.</span>
      </h2>
    </div>
    <VueAirTable class="body" :base="base" :baseId="baseId"></VueAirTable>
  </div>
</template>

<script>
import VueAirTable from "./components/VueAirTable";
export default {
  name: "app",
  components: {
    VueAirTable
  },
  data: function() {
    return {
      base: "Blocks",
      baseId: "appJzuNfkxcKOVhZU"
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#TopBar {
  position: relative;
  background-position: center;
  -webkit-background-size: cover;
  background-size: cover;
  background-repeat: no-repeat;
  padding-top: 146px;
  padding-bottom: 90px;
  background-color: #2d46c1 !important;
  margin-left: auto !important;
  margin-right: auto !important;
  -webkit-box-flex: 0;
  flex: 0 0 100%;
  max-width: 100%;
  width: 100%;
  min-height: 1px;
  padding-right: 15px;
  padding-left: 15px;
  height: 100%;
  text-align: center !important;
  align-content: center !important;
  align-items: center !important;
}

#TopBar #text {
  color: white !important;
  font-size: 2.7rem;
  font-weight: 900;
  margin-bottom: 0.5rem;
  line-height: 1.2;
  font-family: Montserrat, sans-serif;
  letter-spacing: 0;
}

.payroll-ls {
  letter-spacing: 5px;
  box-sizing: border-box;
  text-align: right !important;
}

.body {
  background-color: #fafbfb;
  display: block;
}
</style>