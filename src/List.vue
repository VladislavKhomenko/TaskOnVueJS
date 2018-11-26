<template>
  <table class="table">
    <thead>
      <tr>
        <th>ID</th>
        <th>name</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
      
      <listItem 
        v-for="item in items"
        :item="item"
        :key="item.id"
        @viewDetails="viewDetails"
      ></listItem>
    </tbody>
  </table>
</template>

<script>
import ListItem from "./ListItem.vue";
import _ from "lodash";

export default {
  components: {
    ListItem
  },
  data() {
    return {
      items: [],
      bottom: false,
    };
  },
  created() {
    window.addEventListener("scroll", () => {
      this.bottom = this.bottomVisible();
    });
    this.fectData();
  },
  methods: {
     bottomVisible() {
      const scrollY = window.scrollY
      const visible = document.documentElement.clientHeight
      const pageHeight = document.documentElement.scrollHeight
      const bottomOfPage = visible + scrollY >= pageHeight
      return bottomOfPage || pageHeight < visible
    },
    fectData() {
      this.$http
        .get('https://api.punkapi.com/v2/beers/random')
        .then(response => {
          let api = response.data[0];
          console.log(api)
          let apiInfo = {
            id: api.id,
            name: api.name,
            desc: api.description,
            img: api.image_url,
            tips: api.brewers_tips,
            tagline: api.tagline,
            food: api.food_pairing
          };

          this.items.push(apiInfo);
          if (this.bottomVisible()) {
            this.fectData();
          }
        });
    },
    viewDetails(id) {
      let itemToView = _.find(this.items, { id: id });
      this.$emit("viewDetails", itemToView);
    }
  },
  watch: {
    bottom(bottom) {
      if (bottom) {
        this.fectData();
      }
    }
  }
};
</script>

<style>
</style>
