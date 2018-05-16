<template>
  <div id="app">
    <topbar class="title"></topbar>
    <main>
      <editor class="et"></editor>
      <preview class="view"></preview>
    </main>
  </div>
</template>

<script>
import Editor from './components/Editor'
import Preview from './components/Preview'
import Topbar from './components/Topbar'

export default {
  components: {
    'topbar': Topbar,
    'preview': Preview,
    'editor': Editor
  }
}
</script>
<style>
#app{
  height: 100vh;
  display: flex;
  flex-direction: column;
}
.title{
  background: red;
}
main{
  background: green;
  display: flex;
  flex: 1;
}
main > .et{
  width: 20em;
}
main > .preview{
  flex: 1;
}

</style>
