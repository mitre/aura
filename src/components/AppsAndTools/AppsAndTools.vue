<template>
  <v-container fluid>
    <v-row class="ma-0">
      <v-col class="pa-0">
        <sec :topic="appsAndTools" :md="4" :lg="4" :xl="4" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Section from "@/components/common/BasicCard/Section.vue";
import appsAndTools from "@/assets/data/appsAndTools.json";

export default {
  data() {
    return {
      appsAndTools,
    };
  },
  components: {
    Sec: Section,
  }
};
</script>
