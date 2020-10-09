<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  methods: {}
};
</script>

<style lang="scss" scoped>
div {
  cursor: pointer;
  padding: 2rem;
  border: 2px solid darken($color: #ffffff, $amount: 10);
  border-radius: 5px;

  display: flex;
  justify-content: center;
  align-items: center;

  &:hover {
    background-color: rgba(#e74c3c, 0.15);
  }
}

h3 {
  font-family: "Dynalight", cursive;
  font-size: 4rem;
  color: darken($color: #ffffff, $amount: 60);
}
</style>
