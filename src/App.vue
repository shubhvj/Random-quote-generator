<template>
  <div id="app">
    
    <HelloWorld></HelloWorld>
    <router-view/>
  </div>
</template>

<script>
  import HelloWorld from "@/components/HelloWorld"
  
  export default {
    name: 'app',
    props: {
      msg: String
    },
    components: {
      HelloWorld
    }
  }
  </script>
<style>
body{
  height: 100%;
}
</style>
