<template>
  <div class="container">
    <app-header :maxQuote="maxQuote" :quoteLength="quotes.length"></app-header>
    <app-new-quote @addQuoteItem="addNewQuote"></app-new-quote>
    <app-quote-grid :quoteListItems="quotes" @deleteQuote="deleteQuote"></app-quote-grid>
  </div>
</template>

<script>
import quoteGrid from "@/components/quoteGrid.vue";
import newQuote from "@/components/newQuote.vue";
import Header from "@/components/Header.vue";
export default {
  data() {
    return {
      quotes: ["This is forst Quote"],
      maxQuote: 3
    };
  },
  components: {
    "app-quote-grid": quoteGrid,
    "app-new-quote": newQuote,
    "app-header": Header
  },
  methods: {
    newQuote() {
      this.quotes = [];
    },
    addNewQuote(quoteItem) {
      if (this.quotes.length >= this.maxQuote) {
        if (confirm("You quote list ended!! Start New Quote List")) {
          this.newQuote();
        }
      }
      this.quotes.push(quoteItem);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style>
</style>