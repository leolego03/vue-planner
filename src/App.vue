<template>
  <div class="container">
    <Header
      @toggle-add-plan="toggleAddPlan"
      title="Planner"
      :showAddPlan="showAddPlan"
    />
    <router-view :showAddPlan="showAddPlan"></router-view>
    <Footer />
  </div>

</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      showAddPlan: false,
    }
  },
  methods: {
    toggleAddPlan() {
      this.showAddPlan = !this.showAddPlan
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
  background-color: #ffd200;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  /*border: 1px solid #7F7F7F;*/
  padding: 30px 30px 120px;
  border-radius: 5px;
  background-color: #fff;
}

.btn {
  display: inline-block;
  background: #ff8b7f;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
  height: 43px;
}

</style>
