<template>
  <v-container fluid class="pa-0">
    <v-row justify="center" align="center" class="mx-0">
      <v-col cols="12" lg="10" class="pa-0 ma-0">
        <Header>
          <h3 slot="title">Our Training</h3>
          <div class="mt-2" slot="subtitle">
            The MITRE SAF team regularly offers training courses for developing
            automated validation tests using InSpec. Dates and sign-up links for
            future courses are posted on this page when training dates are
            finalized. See below for course materials and recordings.
          </div>
        </Header>
      </v-col>
    </v-row>
    <v-row justify="center" align="center" class="ma-0">
      <v-col cols="12" lg="10" class="pa-0">
        <pastTraining />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import pastTraining from "../components/training/traininginfo";
  import Header from "@/components/core/Header.vue";
  import communityData from "@/assets/data/communityData.json";

  export default {
    data() {
      return {
        communityData: communityData,
      };
    },
    components: {
      Header,
      pastTraining,
    },
    created() {
      let metaThemeColor = document.querySelector("meta[name=theme-color]");
      if (this.$vuetify.theme.dark) {
        metaThemeColor.setAttribute("content", "#212121");
      } else {
        metaThemeColor.setAttribute("content", "#0277bd");
      }
    },
  };
</script>
