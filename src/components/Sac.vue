<template>
  <div class="sac-wrapper">
    <button class="sac-btn" type="button">Click</button>
    <div class="sac-overlay">
      <div class="sac-modal">
        <header>Modal title</header>
        <div class="sac-modal-body">
          <div class="sac-modal-tooltip">Tools</div>
          <div class="sac-modal-items">
            <div class="sac-item">
              <div class="sac-item-label">
                <font-awesome-icon
                  @click="expanded = !expanded"
                  class="sac-item-toggle-icon"
                  :icon="['fas', toggleIconClass]"
                />
                <span class="sac-item-label-text">Item 1</span>
              </div>
              <div class="sac-item-children" v-if="expanded">
                <div class="sac-item">
                  <div class="sac-item-label">Item 1.1</div>
                </div>
                <div class="sac-item">
                  <div class="sac-item-label">Item 1.2</div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <footer>Footer</footer>
      </div>
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
  name: "Sac",
  components: {
    "font-awesome-icon": FontAwesomeIcon
  },
  data: () => ({
    expanded: true
  }),
  computed: {
    toggleIconClass: function() {
      return this.expanded ? "caret-right" : "caret-down";
    }
  }
};
</script>

<style lang="scss" scoped>
$items-margin-left: 10px;

.sac-overlay {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
.sac-modal {
  position: fixed;
  max-width: 90%;
  max-height: 90%;
  background-color: #fafafa;
  border-radius: 4px;
  padding: 15px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.sac-modal-items {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  margin: 0 (-$items-margin-left);
}
.sac-item {
  margin-left: $items-margin-left;
}
.sac-item-toggle-icon {
  margin-right: 5px;
  cursor: pointer;
}
</style>
