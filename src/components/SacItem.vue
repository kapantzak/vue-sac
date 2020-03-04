<template>
  <div class="sac-item">
    <div class="sac-item-label">
      <font-awesome-icon
        v-if="hasChildren"
        @click="expanded = !expanded"
        class="sac-item-toggle-icon"
        :icon="['fas', toggleIconClass]"
      />
      <span class="sac-item-label-text">{{ item.text }}</span>
    </div>
    <div class="sac-item-children" v-if="hasChildren && expanded">
      <sac-item v-for="child in item.children" :key="child.id" v-bind:item="child" />
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { library } from "@fortawesome/fontawesome-svg-core";
import { faCaretDown, faCaretRight } from "@fortawesome/free-solid-svg-icons";

library.add(faCaretDown);
library.add(faCaretRight);

export default {
  name: "SacItem",
  props: ["item"],
  components: {
    "font-awesome-icon": FontAwesomeIcon
  },
  data: () => ({
    expanded: true
  }),
  computed: {
    toggleIconClass: function() {
      return this.expanded ? "caret-right" : "caret-down";
    },
    hasChildren: function() {
      return (this.item.children || []).length > 0;
    }
  }
};
</script>
