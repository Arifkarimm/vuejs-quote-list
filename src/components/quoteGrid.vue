<template>
  <div class="row">
    <app-quote
      v-bind:key="quote"
      v-for="(quote, index) in quoteListItems"
      @click.native="deleteQuote(index)"
    >{{ quote }}</app-quote>
  </div>
</template>

<script>
import quote from "@/components/quote.vue";
export default {
  props: ["quoteListItems", "maxQuote", "quoteLength"],
  components: {
    "app-quote": quote
  },
  methods: {
    deleteQuote(index) {
      this.$emit("deleteQuote", index);
    }
  }
};
</script>

<style scoped>
</style>