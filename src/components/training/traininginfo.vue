<template>
  <v-container fluid>
    <v-row
      align="center"
      justify="center"
      class="ma-0"
      v-for="(course, i) in trainingData.courses"
      :key="i"
    >
      <v-col class="px-0">
        <p class="header my-2">{{ course.name }}</p>
        <p class="ma-2">{{ course.desc }}</p>
        <ul class="my-2">
          <li v-for="(bullet, j) in course.bullets" :key="j" class="ms-2">
            {{ bullet }}
          </li>
        </ul>
        <v-btn
          v-if="course.course_link"
          class="ma-2"
          outlined
          :href="course.course_link"
          target="_blank"
          ><v-icon class="mr-2">mdi-file-document</v-icon>Course
          Materials</v-btn
        >
        <v-btn
          v-if="course.video_link"
          class="ma-2"
          outlined
          :href="course.video_link"
          target="_blank"
          ><v-icon class="mr-2">mdi-play</v-icon>Course Recording</v-btn
        >
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import communityData from "@/assets/data/communityData.json";
  import trainingData from "@/assets/data/trainingData.json";
  import resources from "@/assets/data/resources.json";
  // import RSVPBlock from "@/components/training/RSVPBlock.vue"
  export default {
    name: "App",
    data: () => ({
      communityData: communityData,
      trainingData: trainingData.training,
      resources: resources,
      dialog: false,
      dialogData: {
        name: "",
        date: "",
        link: "",
      },
    }),
    computed: {
      color_mode() {
        if (this.$vuetify.theme.dark) return "darkModeContainer";
        return "lightModeContainer";
      },
      // pastTrainings() {
      //   return this.trainingData.pastTraining.introTraining.concat(this.trainingData.pastTraining.advTraining);
      // },
    },
    // components: {
    //   RSVPBlock
    // },
    methods: {
      passItemData(item) {
        this.dialogData = item;
      },
    },
  };
</script>
