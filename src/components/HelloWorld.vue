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
            v-if="item.img"
            class="iconimg"
            :src="
              currentTabIndex == index && !item.dock ? item.activeImg : item.img
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
          {{ item.title }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
// import {useRouter, useRoute} from 'vue-router'
export default {
  name: "tabBar",
  props: {
    current: {
      type: [Number, String],
      default: 0,
    },
    bgcolor: {
      type: String,
      default: "#fff",
    },
    color: {
      type: String,
      default: "#999",
    },
    activeColor: {
      type: String,
      default: "#22d59c",
    },
    fixed: {
      type: [Boolean, String],
      default: false,
    },
    tabs: {
      type: Array,
      default: () => null,
    },
  },
  emits: {
    click: null,
  },
};
</script>