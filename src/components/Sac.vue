<template>
  <div class="sac-wrapper">
    <button class="sac-btn" type="button">Click</button>
    <div class="sac-overlay">
      <div class="sac-modal">
        <header>Modal title</header>
        <div class="sac-modal-body">
          <div class="sac-modal-tooltip">Tools</div>
          <div class="sac-modal-items">
            <sac-item v-for="item in data" :key="item.id" v-bind:item="item" />
          </div>
        </div>
        <footer>Footer</footer>
      </div>
    </div>
  </div>
</template>

<script>
import SacItem from "./SacItem";

export default {
  name: "Sac",
  components: {
    "sac-item": SacItem
  },
  data: () => ({
    data: [
      {
        id: 1,
        text: "Item 1",
        children: [
          {
            id: 2,
            text: "Item 2"
          },
          {
            id: 3,
            text: "Item 3"
          }
        ]
      },
      {
        id: 4,
        text: "Item 4",
        children: [
          {
            id: 5,
            text: "Item 5",
            children: [
              {
                id: 7,
                text: "Item 7"
              }
            ]
          }
        ]
      },
      {
        id: 6,
        text: "Item 6"
      }
    ]
  })
};
</script>

<style lang="scss">
$items-margin-left: 15px;

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
  padding: 15px 0;
}
.sac-item > .sac-item-children > .sac-item {
  padding-left: 15px;
}
.sac-item-toggle-icon {
  margin-right: 5px;
  cursor: pointer;
}
</style>
