<template>
  <div class="new__quote">
    <h3>Quote</h3>
    <form>
      <textarea v-model="quote"></textarea>
      <button @click.prevent="addQuote">Add Quote</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      quote: ""
    };
  },
  methods: {
    addQuote() {
      this.$emit("newQuote", this.quote);
      this.quote = "";
    }
  }
};
</script>

<style lang="scss" scoped>
.new__quote {
  margin: 2rem auto;
  width: 40%;

  h3 {
    font-size: 1.5rem;
    color: lighten($color: #000000, $amount: 20);
    margin-bottom: 1rem;
  }

  form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    textarea {
      align-self: stretch;
      padding: 2rem;
      outline: none;
      border: 2px solid darken($color: #ffffff, $amount: 10);
      border-radius: 5px;
      margin-bottom: 2rem;
    }

    button {
      cursor: pointer;
      padding: 1rem 2rem;
      border: 0;
      background: linear-gradient(to right, #373b44, #4286f4);
      color: #f2f2f2;
      border-radius: 5px;
    }
  }
}
</style>
