<template>
  <button class="next-button" @click="nextStep">Next step</button>
</template>
  
  <script>
export default {
  methods: {
    nextStep() {
      this.$emit("next");
    },
  },
};
</script>
  
  <style scoped>
.next-button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
}
</style>