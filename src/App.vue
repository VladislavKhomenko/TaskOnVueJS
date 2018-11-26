<template>
  <div class="container">

    <list @viewDetails="viewDetails"></list>
    
    <modal 
      v-show="visible" 
      :item="selectedItem"
      @close="closeModal">
    </modal>
  </div>
</template>

<script>
import List from "./List.vue";
import Modal from "./Modal.vue";

export default {
  components: {
    List,
    Modal
  },
  data() {
    return {
      selectedItem: {},
      visible: false
    }
  },
  methods: {
    viewDetails(item) {
      this.selectedItem = item;
      this.visible = true;
    },
    closeModal() {
      this.visible = false;
    }
  }
}
</script>

<style>
</style>
