<template>
  <v-hover v-slot:default="{ hover }">
    <v-card
      outlined
      class="pa-2"
      style="width: 100%; height: 100%;"
      :to="item.router_link"
      :href="item.link"
      :target="item.link ? '_blank' : '_self'"
      :color="hover && (item.router_link || item.link) ? 'grey' : ''"
    >
      <v-icon v-if="item.icon" large style="font-size:300%" class="mt-2" :color="hover && (item.router_link || item.link) ? '#1a73e8' : ''">{{ item.icon }}</v-icon>
      <v-img
        v-if="item.graphic"
        :src="require('@/assets/img/gif/' + item.graphic + '.gif')"
        class="ma-2"
        max-height="328"
      />
      <v-img
        v-else-if="item.graphic_frame"
        v-bind:src="require('@/assets/img/gif/' + item.graphic_frame)"
        class="ma-2"
        max-height="328"
      />
      <v-card-title class="mt-2 title align-bottom justify-center break-word" :style="hover && (item.router_link || item.link) ? 'color:#1a73e8' : ''">
        <v-icon class="mr-2" :color="hover && (item.router_link || item.link) ? '#1a73e8' : ''">{{ item.side_icon }}</v-icon>
        {{ item.name.replace(/_/, " ") }}
      </v-card-title>
      <v-spacer />
      <v-card-text v-if="item.desc" class="pa-2 body-1">{{ item.desc }}</v-card-text>
      <v-card-text v-if="item.bullets" class="text-left">
        <ul
          v-for="bullet in item.bullets"
          :key="bullet"
          class="body-1"
        >• {{ bullet }}</ul>
      </v-card-text>
      <v-spacer />
      <div justify="center" v-if="item.shields" class="mt-2">
        <img v-for="shield in item.shields" :key="shield" class="ms-2" :src="shield" />
      </div>
      <v-card-actions v-if="(item.app_link || item.doc_link || item.github_link)" class="pa-0">
        <v-container row dense>
          <v-row justify="center">
            <v-col class="pa-0">
              <span v-for="(link, index) in [item.app_link, item.doc_link, item.github_link]" :key="index">
                <v-tooltip top v-if="link">
                  <template v-slot:activator="{ on }">
                    <v-btn
                      color="primary"
                      :href="link"
                      target="_blank"
                      text
                      v-on="on"
                    >
                      <v-icon>{{ ["mdi-desktop-classic", "mdi-file-document", "mdi-github"][index] }}</v-icon>
                    </v-btn>
                  </template>
                  <span>{{ ["Demo", "Documentation", "Github"][index] }}</span>
                </v-tooltip>
              </span>
            </v-col>
          </v-row>
        </v-container>
      </v-card-actions>
    </v-card>
  </v-hover>
</template>

<script>
export default {
  props: {
    item: Object
  },
};
</script>
