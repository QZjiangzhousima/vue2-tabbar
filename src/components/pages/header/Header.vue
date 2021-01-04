<template>
  <div class="tab-bar" :class="{ fixed: fixed }">
    <div
      class="tab-bar__wrap flexbox flex-alignc"
      :style="{ background: bgcolor }"
    >
      <div
        v-for="(item, index) in tabs"
        :key="index"
        class="navigator"
        :class="currentTabIndex == index ? 'on' : ''"
        @click="switchTabs(index, item)"
      >
        <div class="ico" :class="{ dock: item.dock }">
          <i
            v-if="item.dock"
            class="dock-bg"
            :style="{ background: item.dockBg ? item.dockBg : activeColor }"
          ></i>
          <i
            v-if="item.icon"
            class="iconfont"
            :class="item.icon"
            :style="{
              color:
                currentTabIndex == index && !item.dock ? activeColor : color,
              'font-size': item.iconSize,
            }"
          ></i>
          <img
            v-if="item.iconImg"
            class="iconimg"
            :src="
              currentTabIndex == index && !item.dock
                ? item.selectedIconImg
                : item.iconImg
            "
            :style="{ 'font-size': item.iconSize }"
          />
          <em v-if="item.badge" class="nuxt__badge">{{ item.badge }}</em>
          <em v-if="item.dot" class="nuxt__badge-dot"></em>
        </div>
        <div
          class="txt"
          :style="{ color: currentTabIndex == index ? activeColor : color }"
        >
          {{ item.text }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        current: { type: [Number, String], default: 0 },
        // 背景颜色
        bgcolor: { type: String, default: '#fff' },
        // 颜色
        color: { type: String, default: '#999' },
        // 点击后颜色
        activeColor: { type: String, default: '#22d59c' },
        // 是否固定
        fixed: { type: [Boolean, String], default: false },
        // tab选项
        tabs: {
            type: Array,
            default: () => null
        }
    },
    data() {
      return {
          currentTabIndex: this.current
      }
    },
    created() {
        // const _pagePath = this.$route.path
        // this.tabs.map((val, index) => {
        //     if(val.pagePath == _pagePath) {
        //         this.currentTabIndex = index
        //     }
        // })
    },
    methods: {
        switchTabs(index, item) {
            this.currentTabIndex = index
            this.$emit('click', index)
            if(item.pagePath) {
                this.$router.push(item.pagePath)
            }
        }
    },
  }
</script>

<style>
</style>