<template>
  <v-select
    :value="value"
    :disabled="readonly"
    :id="name"
    :options="choices"
    :placeholder="options.placeholder"
    @input="$emit('input', $event)"
  ></v-select>
</template>

<script>
import mixin from "@directus/extension-toolkit/mixins/interface";

export default {
  mixins: [mixin],
  computed: {
    choices() {
      const interfaces = this.$store.state.extensions.interfaces || {};

      let choices = {};

      Object.keys(interfaces).forEach(key => {
        choices[key] = this.$helpers.formatTitle(key);
      });

      return choices;
    }
  }
};
</script>

<style lang="scss" scoped>
.v-select {
  margin-top: 0;
  max-width: var(--width-medium);
}
</style>
