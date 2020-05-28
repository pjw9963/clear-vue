<template>
  <div id="app">
    <div id="list-container">
      <ProList />
      <ConList />
    </div>
  </div>
</template>

<script>
import ProList from './components/ProList.vue'
import ConList from './components/ConList.vue'

export default {
  name: 'App',
  components: {
    ProList,
    ConList
  }
}
</script>

<style>
#list-container {
  display:flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>
