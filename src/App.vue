<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
      <Editor class="editor"/>
      <Preview class="preview"/>
    </main>
  </div>
</template>

<script>
import Topbar from "./components/Topbar";
import Editor from "./components/Editor";
import Preview from "./components/Preview";

export default {
  components: {
    Topbar,
    Preview,
    Editor
  }
};
</script>

<style lang="scss">
html,body,#app{
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
main{
  display: flex;
  flex: 1;
  .editor{
    width: 20em;
  }
  .preview{
    flex: 1;
  }
}
</style>
