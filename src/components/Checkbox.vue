<template>
  <div class="checkbox-container">
    <label :class="selected ? 'label active' : 'label'">
      <div class="cercle">
        <img :src="iconSrc" :alt="value" />
      </div>

      <div class="text">{{ title }}</div>

      <input
        class="input"
        type="checkbox"
        :id="title"
        :value="value"
        :checked="selected"
        @change="handleChange"
      />
    </label>
  </div>
</template>
  
<script>
export default {
  props: {
    id: {
      type: Number,
      required: true,
    },
    iconSrc: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
    selected: {
      type: Boolean,
      required: true,
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
  
<style scoped lang="scss">
@import "../assets/styles/vars";
.step2 {
  .label {
    display: flex;
    align-items: center;
    gap: 12px;
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
  .cercle {
    @extend %f-cc;
    width: 67px;
    height: 67px;
    border-radius: 50%;
    background-color: rgba(74, 58, 255, 0.15);
  }
  .input {
    width: 1px;
    height: 1px;
    overflow: hidden;
    clip: rect(0 0 0 0);
    position: absolute;
  }
  .checkbox {
    position: absolute;
    width: 21px;
    height: 21px;
    background-color: #ffffff;
    border: 1px solid #d9dbe9;
    border-radius: 2px;
  }
  .text {
    @extend %dms-500;
    color: $black;
    font-size: 18px;
    line-height: 20px;
  }
}
</style>