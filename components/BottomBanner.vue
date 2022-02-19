<template>
  <div>
    <div class="my-2">
      <v-img
        :src="source"
        max-height="75"
        max-width="1120"
        class="rounded-lg shadow-xl"
      ></v-img>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component
export default class BottomBanner extends Vue {
  source =
    "https://cdn.cellphones.com.vn/media/wysiwyg/1-specical-tab-s8-1200x75.png";
}
</script>
<style scoped></style>
