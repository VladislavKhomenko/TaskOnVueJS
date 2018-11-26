<template>
    <tr scope="row">
      
      <th>{{item.id}}</th>
      <th>{{item.name}}</th>
      <th>{{item.desc}}</th>
      
      <th><button class="btn btn-primary" @click="viewDetailsClicked">View Details</button></th> 
    </tr>
</template>

<script>
export default {
  props: {
    item: {}
  },
  data() {
    return {}
  },
  methods: {
    viewDetailsClicked() {
      this.$emit("viewDetails", this.item.id);
    }
  }
}
</script>

<style>
button {
  color: #42b983;
  transition: all 0.5s ease;
}
</style>
