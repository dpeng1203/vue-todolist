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
  position: relative;
  z-index: 1;
  box-shadow: 0 0 3px hsla(0,0,0,0.5);
}
main{
  background: #ddd;
  display: flex;
  flex: 1;
}
.icon {
  width: 1em; height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
main > .et{
  width: 30em;
  margin: 16px 8px 16px 16px;
  border: 1px solid bisque;
  background: #fff;
  box-shadow: 0 0 3px hsla(0,0,0,0.5);
  border-radius: 4px;
  overflow: hidden;
}
main > .view{
  flex: 1;
  margin: 16px 16px 16px 8px;
  border: 1px solid blue;
  background: #fff;
  box-shadow: 0 0 3px hsla(0,0,0,0.5);
  border-radius: 4px;
}
</style>
