<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld bgcolor="#f9f9f9" :tabs="[
  {title:'shouye'},
  {title:'熱門'}
  ]" />
  <TabBar bgcolor="#b6ffff" @click="tabbarClicked" :tabs="[
    {
        icon: 'icon-tianjia',
        text: 'Home',
    },
    {
        icon: 'icon-shezhi',
        text: 'Manage',
        badge: 1
    },
    {
        icon: 'icon-male',
        text: 'Ucenter',
        dot: true
    },
    ]"
/>

  <!-- <view-router></view-router> -->
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TabBar from './components/pages/header/Header.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    TabBar
  }
}
</script>
