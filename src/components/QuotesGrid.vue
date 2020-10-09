<template>
  <div class="grid">
    <app-quote
      v-for="(quote, index) in quotes"
      :key="index"
      @click.native="deleteQuote(index)"
    >
      <h3>{{ quote }}</h3>
    </app-quote>
  </div>
</template>

<script>
import Quote from "./Quote.vue";

export default {
  props: ["quotes"],
  components: {
    appQuote: Quote
  },
  methods: {
    deleteQuote(index) {
      this.$emit("quoteDelete", index);
    }
  }
};
</script>

<style lang="scss" scoped>
.grid {
  margin-bottom: 3rem;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 3rem;
}
</style>
