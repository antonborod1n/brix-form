<template>
  <label :class="selected ? 'label active' : 'label'">
    <div class="box">
      <input
        class="input"
        type="radio"
        name="budget"
        :id="id"
        :value="value"
        :checked="selected"
        @change="handleChange"
      />
      <span class="radio"></span>
    </div>

    <span class="text">{{ text }}</span>
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
        id: this.id,
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
    position: relative;
    display: flex;
    align-items: center;
    padding: 25px;
    width: 284px;
    height: 115px;
    border-radius: 16px;
    border: 2px solid $white2;
    background-color: $white;
    box-shadow: 0px 4px 10px 0px rgba(31, 37, 89, 0.07),
      0px 2px 11px 0px rgba(69, 65, 164, 0.06);
    cursor: pointer;
    -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
    &.active {
      border: 2px solid $accent;
    }
    @media (max-width: 678px) {
      width: 100%;
    }
  }
  .input {
    position: absolute;
    width: 1px;
    height: 1px;
    overflow: hidden;
    clip: rect(0 0 0 0);
    &:checked + .radio {
      border: 7px solid $accent;
    }
  }
  .radio {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
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
    padding-left: 35px;
  }
}
</style> 