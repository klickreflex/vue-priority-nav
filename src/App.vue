<template>
  <div id="app">
    <priority-nav :options="{ navDropdownLabel: 'SHOW ME MORE!' }">
      <ul style="display: inline-block;">
        <li>Foo</li>
        <li>Foo</li>
        <li>Foo</li>
        <li>Haha</li>
        <li>Foo</li>
        <li>Foo</li>
        <li>Foo</li>
        <li>Foo</li>
        <li>Foo</li>
        <li>Foo</li>
      </ul>
    </priority-nav>
  </div>
</template>

<script>
import PriorityNav from './components/priority-nav.vue'

export default {
  name: 'app',
  components: {
    PriorityNav,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
