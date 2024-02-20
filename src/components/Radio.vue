<template>
  <label :class="selected ? 'label active' : 'label'" :for="id">
    <span class="text">{{ text }}</span>

    <input
      class="input"
      type="radio"
      name="budget"
      :id="id"
      :value="value"
      :checked="selected"
      @change="handleChange"
    />
  </label>
</template>


<script>
export default {
  props: {
    id: {
      type: Number,
    },
    title: {
      type: String,
    },
    value: {
      type: String,
    },
    text: {
      type: String,
    },
    selected: {
      type: Boolean,
    },
  },
  methods: {
    handleChange(event) {
      this.$emit("change", {
        id: id,
        selected: event.target.checked,
      });
    },
  },
};
</script>


<style lang="scss" scoped>
@import "../assets/styles/vars";
.step3 {
  .label {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: center;
    width: 284px;
    height: 115px;
    border-radius: 16px;
    border: 1px solid $white2;
    background-color: $white;
    box-shadow: 0px 4px 10px 0px rgba(31, 37, 89, 0.07),
      0px 2px 11px 0px rgba(69, 65, 164, 0.06);
    cursor: pointer;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    &.active {
      border: 2px solid $accent;
    }
  }
  .input {
    width: 1px;
    height: 1px;
    overflow: hidden;
    clip: rect(0 0 0 0);
    position: absolute;
  }
  .radio {
    position: absolute;
    left: 25px;
    width: 25px;
    height: 25px;
    background-color: #ffffff;
    border: 1px solid #d9dbe9;
    border-radius: 50%;
  }
  .text {
    @extend %dms-500;
    color: $black;
    font-size: 18px;
    line-height: 20px;
    padding-left: 60px;
  }
}
</style> 