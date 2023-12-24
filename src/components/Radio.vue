<template>
  <input
    type="radio"
    :id="item.id"
    :value="item.value"
    :checked="item.selected"
    @change="handleChange"
  />
  <label :for="item.id">
    <span class="text">{{ item.text }}</span>
  </label>
  <!-- <input
      class="input"
      type="radio"
      name="money"
      :id="item.id"
      :value="item.value"
      :checked="item.selected"
      @change="handleChange"
    />
    <span class="radio"></span>
    <span class="text">{{ item.text }}</span>
  </label> -->
</template>


<script>
export default {
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  methods: {
    handleChange() {
      this.$emit("change", {
        id: this.item.id,
      });
    },
  },
};
</script>


<style lang="scss" scoped>
@import "../assets/styles/vars";
.step3 {
  .label {
    position: relative;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    width: 284px;
    height: 115px;
    border-radius: 16px;
    border: 1px solid $white2;
    background-color: $white;
    box-shadow: 0px 4px 10px 0px rgba(31, 37, 89, 0.07),
      0px 2px 11px 0px rgba(69, 65, 164, 0.06);
    cursor: pointer;
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
    &:checked + .radio {
      border: 7px solid $accent;
    }
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
</style>  -->