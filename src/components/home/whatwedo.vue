<template>
  <v-container fluid>
    <v-row v-for="(topic, index) in whatwedodata" :key="index">
      <v-col class="pa-0">
        <sec :topic="topic" :md="widths[index][0]" :lg="widths[index][1]" :xl="widths[index][2]" />
        <v-divider v-if="index + 1 < whatwedodata.length" class="ma-2" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Section from "@/components/common/BasicCard/Section.vue";

export default {
  props: {
    whatwedodata: Array
  },
  data() {
    return {
      widths: [[3, 3, 3], [3, 3, 3], [6, 6, 3], [4, 4, 4]],
    };
  },
  components: {
    Sec: Section,
  }
};
</script>
