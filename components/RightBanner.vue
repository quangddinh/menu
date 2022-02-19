v
<template>
  <div class="">
    <div>
      <div class="img-banner">
        <v-img height="100%" class="rounded shadow-2xl" :src="src1"></v-img>
      </div>
      <div class="mt-8 mb-8 img-banner">
        <v-img height="100%" class="rounded shadow-2xl" :src="src2"></v-img>
      </div>
      <div class="img-banner">
        <v-img height="100%" class="rounded shadow-2xl" :src="src3"></v-img>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component
export default class Slider extends Vue {
  src1 = "https://cdn.cellphones.com.vn/media/ltsoft/promotion/flip_right.png";
  src2 = "https://cdn.cellphones.com.vn/media/ltsoft/promotion/13-desk.png";
  src3 = "https://cdn.cellphones.com.vn/media/ltsoft/promotion/ltRB.png";
}
</script>
<style scoped>
.img-banner {
  width: 265px;
  height: 115px;
}
</style>
