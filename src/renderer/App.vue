<template>
  <div id="app">
    <router-view
      :server="manager.servers[serverId]"
      :serverNameList="serverNameList"
      :isDefault="serverId === 0"
      @updateServer="saveData()">
    </router-view>
  </div>
</template>

<script>
  export default {
    name: 'photon',
    props: ['manager'],
    data: function () {
      return {
        serverId: 0
      }
    },
    computed: {
      serverNameList: function () {
        return this.manager.servers.map(server => {
          return server.name
        })
      }
    },
    methods: {
      saveData: function () {
        this.manager.writeStorage()
      }
    }
  }
</script>

<style>
  body {
    margin: 0px;
    background-color: #fff;
    font-family: "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
  }

  input, output, textarea, select, button {
    font-family: "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "Heiti SC", "Microsoft YaHei", "WenQuanYi Micro Hei", sans-serif;
  }
</style>
