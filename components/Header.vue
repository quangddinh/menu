<template>
  <div>
    <div class="bg-red-600 sm:flex-row flex-col flex justify-center">
      <div class="flex justify-center sm:my-3">
        <div class="sm:block hidden">
          <v-icon large color="#ffff">mdi-text-box-outline</v-icon>
        </div>
        <div style="height: 40px" class="cursor-pointer">
          <img :src="img" style="height: 100%" alt="" />
        </div>
        <!-- dropdown location -->
        <v-menu offset-y>
          <template v-slot:activator="{ on, attrs }">
            <div v-bind="attrs" v-on="on">
              <div class="flex sm:mx-1 sm:p-1 red-hover">
                <div><v-icon color="#ffff">mdi-map-marker-outline</v-icon></div>
                <div>
                  <div class="text-white" style="font-size: 10px">
                    Xem giá tại
                  </div>
                  <div class="text-white text-xs">
                    {{ location }}
                    <span>
                      <v-icon color="#ffff">mdi-chevron-down</v-icon></span
                    >
                  </div>
                </div>
              </div>
            </div>
          </template>
          <v-list>
            <v-list-item v-for="(item, index) in items" :key="index">
              <v-list-item-title
                class="text-xs cursor-pointer"
                @click="getLocation(index)"
                ><span><v-icon color="#000000">mdi-map-marker</v-icon></span>
                {{ item.title }}</v-list-item-title
              >
            </v-list-item>
          </v-list>
        </v-menu>
        <!-- search bar -->
        <div style="width: 290px" class="sm:block hidden sm:mx-1 sm:p-1">
          <v-text-field
            placeholder="Bạn cần tìm gì?"
            prepend-inner-icon="mdi-magnify"
            class="bg-white"
            dense
            solo
            rounded
            hide-details="auto"
          ></v-text-field>
        </div>
        <!-- phone -->
        <div>
          <div
            class="sm:flex cursor-pointer sm:block hidden sm:mx-1 sm:p-1 red-hover"
          >
            <div><v-icon color="#ffff">mdi-phone</v-icon></div>
            <div>
              <div class="text-white text-xs">Gọi mua hàng</div>
              <div class="text-white text-sm font-bold">1800.2097</div>
            </div>
          </div>
        </div>
        <!-- store -->
        <div>
          <div
            class="sm:flex cursor-pointer sm:block hidden sm:mx-1 sm:p-1 red-hover"
          >
            <div><v-icon color="#ffff">mdi-map-marker-outline</v-icon></div>
            <div>
              <div class="text-white text-xs">
                <div>Cửa hàng</div>
                <div>gần bạn</div>
              </div>
            </div>
          </div>
        </div>
        <!-- shipping -->
        <div>
          <div
            class="sm:flex cursor-pointer sm:block hidden sm:mx-1 sm:p-1 red-hover"
          >
            <div><v-icon color="#ffff">mdi-phone</v-icon></div>
            <div>
              <div class="text-white text-xs">
                <div>Tra cứu</div>
                <div>đơn hàng</div>
              </div>
            </div>
          </div>
        </div>
        <!-- shipping -->
        <div>
          <div
            class="sm:flex cursor-pointer sm:mx-1 sm:p-1 sm:flex-col flex-row red-hover"
          >
            <div><v-icon color="#ffff">mdi-cart</v-icon></div>
            <div>
              <div class="text-white text-xs">
                <div>Giỏ</div>
                <div>hàng</div>
              </div>
            </div>
          </div>
        </div>
        <!-- smember -->
        <div
          class="text-center cursor-pointer bg-red-500 sm:block hidden sm:mx-1 sm:p-1"
        >
          <div><v-icon color="#ffff">mdi-account-circle-outline</v-icon></div>
          <div>
            <div class="text-white text-xs">Smember</div>
          </div>
        </div>
      </div>
      <div class="sm:hidden block pb-5 w-11/12 mx-1">
        <v-text-field
          placeholder="Bạn cần tìm gì?"
          prepend-inner-icon="mdi-magnify"
          class="bg-white"
          dense
          solo
          rounded
          hide-details="auto"
        ></v-text-field>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from "vue-property-decorator";

@Component
export default class Header extends Vue {
  items = [{ title: "Miền Nam" }, { title: "Miền Bắc" }];
  location = this.items[0].title;
  onclick = false;
  getLocation(index: number) {
    this.location = this.items[index].title;
  }
  img =
    "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAhIAAABfCAYAAAC9ZC4kAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6REQzNUE1OThENjI3MTFFQUJDOTI5NjNDMjAyQkNFMkQiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6REQzNUE1OTlENjI3MTFFQUJDOTI5NjNDMjAyQkNFMkQiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDpERDM1QTU5NkQ2MjcxMUVBQkM5Mjk2M0MyMDJCQ0UyRCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDpERDM1QTU5N0Q2MjcxMUVBQkM5Mjk2M0MyMDJCQ0UyRCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PtMJt2kAAAPtSURBVHja7Nzbbts6FEDB0ND//zL7mhg1oqoSuS8zjwdBj8SbV4RYY875BQBwxcsQAABCAgAQEgCAkAAAhAQAgJAAAB5wGIJyznyfdwT4N7vPg/GCOGdid/91HnkiYWPZhHvG17gCJXgiAYDfuv3Sc5knEgCAkAAAhAQAICQAACEBACAkAAAhAQAICQCgBi+kAoCfMr95dvmLtzyRAACEBAAgJAAAIQEACAkAACEBAAgJAEBIAABCAgBo7uk3W+54O9hIeu3Dcty2ZnaN/yx6b7PovM3C69F5l/M+QryB86h8c8muezaPihno/z8Kj+0oNn9P39s0Z/Zb8JDZ/nl7FFqYla57NtpgM/A1jaLjPYrO393zNt2X/SYmfvd6YDH4IDOmVe5vFh73WXh8ZpDxibgenXeEDQkRYXOJnV73JgLNmXmLY+vTHN/awIFB1bmb1iViIkdIeBrhWn1wujdjIZCczU1j4uh2wwGu28F9fQxGwY1v7p7/APVHfM67p/dE6zV2JFuUFaJn+FAz/o0Owifmzrzlm7Pq89Y6JlaGxAg26RGue3w5FLuP/9i4trPO3RPzNjff45Pz5rwTE4/yx5Z54sf4u7+z/+YIMHaj+Nq4e4w7zFkHLX8xfFmgPiyxtjCuxu6262wXE55IAMT5IBQpseb66pOiVjEhJADgXFSICSEBAMuCokVMCAkAuBYUZ6JiVg8MIbGfr38C5I+KKzFR4vw/rAEf8gDOu1uC4rdwGN9+dr79bNo/tPVEAgDuj4px4mfeQyNlzAkJAHg2KD693v1vsZEuKIQEAKyLijMxkSoohAQArA2KM//tPSjCRoWQAICYgfEpKoQEAHApJsIFha9/3jOpAM47Vgvx1VFPJAAgd9BtfUIhJAAgf0x87YoJIQEAdWJCSAAAeWJiVUh4hzsAFIwJTyQEEIDzTkykCIlpc2Fuja25syeo5bVhkUZYqMPman9YmtOc42zunHcEs+uFVDPQpsmyuTq+LMaBZh7pOWdejpXIq/GEW6hYK/XHwtwZh6shJYAXhgQ4gI2J6wQh0XLDOmgAAcgnnkosDAkxQcVD19rIOT7mznknJpKGROYNbHNhPdQYK3NnjMTEYsfDC3Um3VwWjcOVXPvd/DnvVsSEdbYwJLJv7syLZRQaC+sn17XYNzmvxYejmAgdEgBQLSb4xtc/AQAhAQAICQBASAAAQgIAQEgAAEICABASAICQAACa82ZLAPjJa7D/gScSAICQAACEBAAgJAAAIQEAICQAACEBAAgJAKAGL6QCoINpCIQEdXhrHLDyvBERQgIA/PISkb+RAACEBAAgJAAAIQEAdPBHgAEAruC43nH9c2MAAAAASUVORK5CYII=";
}
</script>
<style scoped>
.drop-down {
  position: fixed;
  left: 40%;
}
.red-hover:hover {
  background-color: #df3346;
  border-radius: 10px;
}
</style>
<style>
.v-input__control .v-input__slot {
  border-radius: 10px !important;
}
</style>
