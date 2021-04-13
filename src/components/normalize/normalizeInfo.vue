<template>
  <v-container fluid pa-0>
    <div v-for="(row, index) in normalize_data" :key="index">
      <p class="header">{{ row.header }}</p>
      <p class="ma-2">
        <span v-html="row.desc" />
      </p>
      <ul v-if="row.bullets" class="ma-2">
        <li v-for="(bullet, index) in row.bullets" :key="index">
          <a v-if="bullet.link" :href="bullet.link" target="_blank">{{
            bullet.main
          }}</a>
          <div v-else>{{ bullet.main }}</div>
          <ul v-if="bullet.sub">
            <li v-for="(sub_bullet, index) in bullet.sub" :key="index">
              {{ sub_bullet }}
            </li>
          </ul>
        </li>
      </ul>
      <div v-if="row.examples">
        <div v-for="ex in row.examples" :key="ex" class="ma-4">
          <p class="subheader ma-0">{{ ex.title }}</p>
          <p>{{ ex.desc }}</p>
          <Prism language="ruby">{{ ex.code }}</Prism>
        </div>
      </div>
      <p v-if="row.footer" class="ma-2">
        <span v-html="row.footer" />
      </p>
    </div>
  </v-container>
</template>

<script>
import normalize_data from "@/assets/data/normalize.json";
import "prismjs";
import "prismjs/components/prism-ruby.js";
import "prismjs/components/prism-markup.js";
import Prism from "vue-prism-component";
import 'prismjs/themes/prism-tomorrow.css';

export default {
  data() {
    return {
      normalize_data: normalize_data.normalize,
    };
  },
  components: {
    Prism,
  },
};
</script>

<style scoped>
.header {
  font-size: 150%;
  font-weight: bold;
  color: #1a73e8;
}
.subheader {
  font-size: 125%;
  font-weight: bold;
  color: #1a73e8;
}

code {
  background-color: #292929;
}
</style>
