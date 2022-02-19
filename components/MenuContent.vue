<template>
  <div>
    <div class="flex flex-col justify-center">
      <div class="justify-center">
        <div class="flex flex-row justify-center">
          <TreeView class="mt-4 sm:block hidden" />
          <Slider class="mx-2" />
          <RightBanner class="mt-5 sm:block hidden" />
        </div>
        <div class="flex flex-row justify-center sm:w-full w-1/12">
          <BottomBanner class="content-center" />
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";
import TreeView from "./TreeMenu.vue";
import Slider from "./Slider.vue";
import RightBanner from "./RightBanner.vue";
import BottomBanner from "./BottomBanner.vue";

@Component({
  components: { TreeView, Slider, RightBanner, BottomBanner },
})
export default class MenuContent extends Vue {
  items = [{ title: "Miền Nam" }, { title: "Miền Bắc" }];
  location = this.items[0].title;
  onclick = false;
  getLocation(index: number) {
    this.location = this.items[index].title;
  }
}
</script>
<style scoped></style>
