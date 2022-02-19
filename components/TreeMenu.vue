<template>
  <div class="tree-menu rounded shadow-2xl">
    <a-menu
      mode="vertical"
      @click="handleClick"
      v-for="item in arrayCategory"
      :key="item"
    >
      <a-sub-menu key="sub1">
        <span slot="title"
          ><span>{{ item.category }}</span></span
        >
        <a-sub-menu key="sub1-2" :title="item.subName">
          <a-menu-item key="5"> {{ item.product }}</a-menu-item>
          <a-menu-item key="6"> {{ item.product }}</a-menu-item>
          <a-menu-item key="7"> {{ item.product }}</a-menu-item>
          <a-menu-item key="8"> {{ item.product }}</a-menu-item>
          <a-menu-item key="9"> {{ item.product }}</a-menu-item>
          <a-menu-item key="10"> {{ item.product }}</a-menu-item>
        </a-sub-menu>
        <a-sub-menu key="sub1-2" :title="item.subName"> </a-sub-menu>
        <a-sub-menu key="sub1-3" :title="item.subName"> </a-sub-menu>
        <a-sub-menu key="sub1-4" :title="item.subName"> </a-sub-menu>
        <a-sub-menu key="sub1-5" :title="item.subName"> </a-sub-menu>
      </a-sub-menu>
    </a-menu>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component
export default class TreeMenu extends Vue {
  mounted() {
    this.initData();
  }

  async initData() {
    const res = await fetch("http://localhost:8888/data")
      .then((response) => response.json())
      .then((data) => (this.arrayCategory = data));
    console.log(this.arrayCategory);
  }
  arrayCategory = [] as any;
  handleClick() {
    console.log("todo");
  }
}
</script>
<style scoped>
.tree-menu {
  padding: 0;
  width: 205px;
  border-radius: 10px !important;
  border: solid #ffff 5px;
}
</style>
<style>
.ant-menu-submenu-title {
  margin: 0 !important;
  height: 30px !important;
}
.v-list-item {
  min-height: 0 !important;
}
</style>
