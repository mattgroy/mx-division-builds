<template>
  <div class="toolbar">
    <span>The division 2 Builds tool</span>
    <div class="spacer"></div>
    <button @click="history.back()">Undo</button>
    <button @click="history.forward()">Redo</button>
    <button @click="saveAndShare()">Save & Share</button>
    <button @click="clear()">Clear</button>
    <button @click="newBuild()">New Build</button>
  </div>
</template>

<script>
import { openSaveShareModal } from "../utils/modalService";

export default {
  name: "Toolbar",
  data() {
    return {
      history
    };
  },
  created() {
    this.history = window.history;
  },
  methods: {
    saveAndShare() {
      openSaveShareModal();
    },
    clear() {
      // TODO: Yeah this should be changed
      this.$router.push({
        name: "home"
      });
      location.reload();
    },
    newBuild() {
      window.open('/','_blank');
    }
  }
};
</script>

<style lang="scss" scoped>
.toolbar {
  display: flex;
}
.spacer {
  flex: 1 1;
}

button {
  margin-left: 8px;
  color: white;
  border: 1px solid white;
  background: transparent;
}
</style>