<template>
  <button class="prev-button" @click="prevStep">Previous step</button>
</template>
  
  <script>
export default {
  methods: {
    prevStep() {
      this.$emit("prev");
    },
  },
};
</script>
  
  <style scoped>
.prev-button {
  background-color: #6c757d;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
}
</style>