<template>
  <div id="app" :class="{previewMode: previewMode}">
    <topbar class="title" @preview="preview"></topbar>
    <main>
      <editor class="et" :resume='resume'></editor>
      <preview class="view" :resume='resume'></preview>
    </main>
    <el-button type="primary" id="exit" @click="exit">退出</el-button>
  </div>
</template>

<script>
import Editor from './components/Editor'
import Preview from './components/Preview'
import Topbar from './components/Topbar'

export default {
  data() {
    return {
      previewMode: false,
      resume: {
        profile: {
        name: '',
        city: '',
        birth: ''
        },
        workHistory: [
          {company: '',content: ''}
        ],
        studyHistory: [
          {school: '',duration: '',degree: ''}
        ],
        projects: [
          {name: '',content: ''}
        ],
        awards: [
          {name: ''}
        ],
        contacts: {
          qq: '',
          wechat: '',
          telephone: ''
        }
      }
    }
  },
  components: {
    'topbar': Topbar,
    'preview': Preview,
    'editor': Editor
  },
  methods: {
    preview () {
      this.previewMode = true
    },
    exit(){
      this.previewMode = false
    }
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

.previewMode > #topbar{
  display: none;
}
.previewMode #editor{
  display: none;
}
.previewMode #preview{
  max-width: 800px;
  margin: 16px auto;
}
#exit{
  display: none;
}
.previewMode #exit{
  display: inline-block;
  position: fixed;
  right: 300px;
  bottom: 32px;
}

</style>
