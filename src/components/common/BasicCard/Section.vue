<template>
  <v-container fluid class="ma-0 pa-0">
    <v-row v-if="topic.sectionHeader" class="ma-0">
      <v-col class="pa-0">
        <p class="ma-0 primary--text" style="text-align: center; font-size: 2.5rem;">{{ topic.sectionHeader }}</p>
      </v-col>
    </v-row>
    <v-row v-if="topic.sectionDesc" class="ma-0">
      <v-col class="pa-0">
        <p style="text-align: center">{{ topic.sectionDesc }}</p>
      </v-col>
    </v-row>
    <v-row v-if="topic.image" class="ma-0">
      <v-col class="pa-3">
        <v-card
          :to="topic.image.router_link"
          :href="topic.image.link"
          flat
          outlined
        >
          <v-img :src="require(`@/assets/img/what-we-do/${topic.image.filename}.png`)" />
        </v-card>
      </v-col>
    </v-row>
    <v-row v-if="topic.items" class="ma-0" justify="center">
      <v-col
        v-for="(item, i) in topic.items"
        :key="i"
        :cols="cols"
        :sm="sm"
        :md="md"
        :lg="lg"
        :xl="xl"
        class="text-center pa-1"
      >
        <basic-card :item="item" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import BasicCard from "@/components/common/BasicCard/BasicCard.vue";
export default {
  components: {
    BasicCard
  },
  props: {
    topic: Object,
    cols: {
      default: 12,
    },
    sm: {
      default: 6,
    },
    md: {
      default: 6,
    },
    lg: {
      default: 3,
    },
    xl: {
      default: 3,
    }
  },
};
</script>
