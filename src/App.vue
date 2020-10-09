<template>
  <div class="container">
    <app-header :quotes="quotes" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @newQuote="addQuote"></app-new-quote>
    <app-quotes-grid
      :quotes="quotes"
      @quoteDelete="deleteQuote"
    ></app-quotes-grid>
    <div class="info">
      <h3>Info: Click on a Quote to delete it</h3>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import NewQuote from "./components/NewQuote.vue";
import QuotesGrid from "./components/QuotesGrid.vue";

export default {
  name: "app",
  data() {
    return {
      quotes: ["When nothing goes right, go left"],
      maxQuotes: 10
    };
  },
  components: {
    appHeader: Header,
    appNewQuote: NewQuote,
    appQuotesGrid: QuotesGrid
  },
  methods: {
    addQuote(quote) {
      console.log(this.quotes.length);
      if (this.quotes.length < this.maxQuotes) {
        this.quotes.push(quote);
      } else {
        return alert(
          "Maximum quotes limit reached, please delete some before adding"
        );
      }
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  }
};
</script>

<style lang="scss" scoped>
.container {
  max-width: 1400px;
  height: 100vh;

  margin: auto;
  margin-top: 5rem;
}

.info {
  margin-bottom: 3rem;
  padding: 2rem;
  border-radius: 5px;
  background-color: rgba(#81ecec, 0.3);

  display: flex;
  justify-content: center;
  align-items: center;

  h3 {
    font-size: 1.7rem;
    font-weight: normal;
    color: darken($color: #3498db, $amount: 20);
  }
}
</style>
