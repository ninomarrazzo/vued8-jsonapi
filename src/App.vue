<template>
  <div id="app">
    <layout-header></layout-header>
    <router-view/>
  </div>
</template>

<script>
import LayoutHeader from './components/Layout/LayoutHeader'

export default {
  name: 'App',
  components: {
    LayoutHeader
  }
}
</script>
