<template>
  <div class="quotes__progress">
    <h2>Quotes Added</h2>
    <div class="progress" v-if="quotes.length">
      <div
        class="bar"
        :style="{ width: (quotes.length / maxQuotes) * 100 + '%' }"
      >
        <span>{{ quotes.length }} / {{ maxQuotes }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["quotes", "maxQuotes"]
};
</script>

<style lang="scss" scoped>
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
</style>
