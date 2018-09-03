<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
    <Topbar class="topbar" v-on:preview="preview"/>
    <main>
      <Editor class="editor" v-bind:resume="resume"/>
      <Preview class="preview" v-bind:resume="resume"/>
    </main>
    <el-button id="cancelPreview" v-on:click="cancelPreview()">退出预览</el-button>
  </div>
</template>

<script>
import Topbar from "./components/Topbar";
import Editor from "./components/Editor";
import Preview from "./components/Preview";

export default {
  data() {
    return{
      previewMode: false,
      resume: {
        profile: [{ name: '',city: '',birth: '',sex:''}],
        workExp: [{company:'',position:'',duration:'',content:''}],
        education: [{school: '',duration:'',degree:'',content:''}],
        project: [{name: '',content: ''}],
        contact: [{QQ:'',wechat: '',tel: '',email: ''}]
      }
    }
  },
  methods:{
    cancelPreview(){
      this.previewMode = false
    },
    preview(){
      this.previewMode = true
    }
  },
  components: {
    Topbar,
    Preview,
    Editor
  }
};
</script>

<style lang="scss">
html,
body,
#app {
  height: 100%;
  overflow: hidden;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  height: 100%;
}
.topbar {
  position: relative;
  z-index: 1;
  box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
}
main {
  display: flex;
  flex: 1;
  background: #ddd;
  .editor {
    width: 35em;
    margin: 16px 8px 16px 16px;
    background: white;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
    border-radius: 4px;
    overflow: hidden;
  }
  .preview {
    flex: 1;
    margin: 16px 16px 16px 8px;
    background: white;
    box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
    border-radius: 4px;
    overflow-y: scroll;
  }
}
.icon {
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;
}
.previewMode > #topbar{
  display: none;
}
.previewMode #editor{
  display: none;
}
.previewMode #preview{
  max-width: 800px;
  margin: 32px auto;
}
#cancelPreview{
  display: none;
}
.previewMode #cancelPreview{
  position: absolute;
  display: block;
  top: 30px;
  right: 30px;
}
@media print {
  .previewMode #cancelPreview{
    display: none!important;
  }
  .previewMode #preview{
    margin: 0 auto!important;
    overflow: unset!important;
  }
  body{
    height: auto!important;
    overflow: unset!important;
  }
}
</style>
