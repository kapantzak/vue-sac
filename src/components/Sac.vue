<template>
  <div class="sac-wrapper">
    <button class="sac-btn" type="button">Click</button>
    <div class="sac-overlay">
      <div class="sac-modal">
        <header>Modal title</header>
        <div class="sac-modal-body">test</div>
        <footer>Footer</footer>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Sac",
  data: () => ({
    datasource: [
      {
        id: 1,
        descr: "One"
      }
    ]
  })
};
</script>

<style scoped>
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
</style>