<template>
  <div :class="$vuetify.breakpoint.mdAndDown ? 'pa-2' : 'pt-6'">
    <div
      class="google-font primary--text pa-0 ma-0"
      style="font-weight: 350; font-size: 2.0rem"
    >
      <slot name="title"></slot>
    </div>
    <div class="google-font mx-2 py-0" style="font-size: 1.0rem">
      <slot name="subtitle"></slot>
    </div>
  </div>
</template>
