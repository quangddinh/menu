<template>
  <v-app>
    <Header />
    <MenuContent />
  </v-app>
</template>
<script lang="ts">
import { Vue, Prop, Component } from "vue-property-decorator";
import Header from "../components/Header.vue";
import MenuContent from "../components/MenuContent.vue";
@Component({
  components: { Header, MenuContent },
})
export default class ClassAPI extends Vue {
  source =
    "https://cdn.cellphones.com.vn/media/wysiwyg/1-specical-tab-s8-1200x75.png";
}
</script>
