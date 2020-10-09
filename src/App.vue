<template>
  <div class="container">
    <div class="quotes__progress">
      <h2>Quotes Added</h2>
      <div class="progress" v-if="quotes.length">
        <div class="bar" :style="{ width: quotes.length * 10 + '%' }">
          <span>{{ quotes.length }} / 10</span>
        </div>
      </div>
    </div>
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
    appNewQuote: NewQuote,
    appQuotesGrid: QuotesGrid
  },
  methods: {
    addQuote(quote) {
      this.quotes.push(quote);
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

.quotes {
  &__progress {
    h2 {
      font-size: 2.5rem;
      margin-bottom: 1rem;
      color: lighten($color: #000000, $amount: 20);
    }
  }
}

.progress {
  width: 100%;
  height: 3rem;
  border-radius: 5px;
  background-color: darken($color: #ffffff, $amount: 5);
  overflow: hidden;

  .bar {
    height: 100%;
    background: linear-gradient(to right, #373b44, #4286f4);
    transition: width 0.5s ease-in-out;

    span {
      padding: 0.3rem 0;
      font-size: 1.5rem;
      color: #fff;

      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
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
