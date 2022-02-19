<template>
  <div class="rounded shadow-2xl sm:w-1/3 w-full">
    <v-carousel cycle height="380" show-arrows-on-hover>
      <template v-slot:prev="{ on, attrs }">
        <v-icon v-bind="attrs" v-on="on">mdi-chevron-left</v-icon>
      </template>
      <template v-slot:next="{ on, attrs }">
        <v-icon v-bind="attrs" v-on="on">mdi-chevron-right</v-icon>
      </template>
      <v-carousel-item v-for="(slide, i) in items" :key="i">
        <v-sheet height="100%">
          <v-row class="fill-height" align="center">
            <v-img :src="items[i].src"></v-img>
          </v-row>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component
export default class Slider extends Vue {
  slides = ["First", "Second", "Third", "Fourth", "Fifth"];
  colors = [
    "indigo",
    "warning",
    "pink darken-2",
    "red lighten-1",
    "deep-purple accent-4",
  ];
  items = [
    {
      src: "https://cdn.cellphones.com.vn/media/ltsoft/promotion/asus.png",
    },
    {
      src: "https://cdn.cellphones.com.vn/media/ltsoft/promotion/mi_eco.png",
    },
    {
      src: "https://cdn.cellphones.com.vn/media/ltsoft/promotion/redmi_buds_3.png",
    },
    {
      src: "https://cdn.cellphones.com.vn/media/ltsoft/promotion/dlbd-690-300-max.png",
    },
    {
      src: "https://cdn.cellphones.com.vn/media/ltsoft/promotion/s22_ultra.png",
    },
    {
      src: "https://cdn.cellphones.com.vn/media/ltsoft/promotion/Apple_watch.png",
    },
  ];
}
</script>
<style scoped>
.ant-carousel >>> .slick-dots {
  height: auto;
}
.ant-carousel >>> .slick-slide img {
  border: 5px solid #fff;
  display: block;
  margin: auto;
  max-width: 80%;
}
.ant-carousel >>> .slick-thumb {
  bottom: -45px;
}
.ant-carousel >>> .slick-thumb li {
  width: 60px;
  height: 45px;
}
.ant-carousel >>> .slick-thumb li img {
  width: 100%;
  height: 100%;
  filter: grayscale(100%);
}
.ant-carousel >>> .slick-thumb li.slick-active img {
  filter: grayscale(0%);
}
</style>
