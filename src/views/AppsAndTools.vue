<template>
  <v-container fluid class="pa-0 ma-0">
    <v-row justify="center" align="center" class="ma-0">
      <v-col cols="12" lg="10" class="pa-0">
        <Header>
          <h3 slot="title">Apps and Tools</h3>
        </Header>
      </v-col>
    </v-row>
    <v-row justify="center" align="center" class="ma-0">
      <v-col
        cols="12"
        lg="10"
        class="pa-0"
        :class="this.$vuetify.theme.dark == true ? 'darkModeContainer' : 'lightModeContainer'"
      >
        <apps-and-tools />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Header from "@/components/core/Header.vue";
import AppsAndTools from "@/components/AppsAndTools/AppsAndTools.vue";

export default {
  components: {
    Header,
    AppsAndTools,
  },
  created() {
    let metaThemeColor = document.querySelector("meta[name=theme-color]");
    if (this.$vuetify.theme.dark) {
      metaThemeColor.setAttribute("content", "#212121");
    } else {
      metaThemeColor.setAttribute("content", "#0277bd");
    }
  }
};
</script>
