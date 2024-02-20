<template>
  <div class="checkbox-container">
    <label
      :class="item.selected ? 'label active' : 'label'"
      :id="item.id"
      :for="item.title"
    >
      <div class="cercle">
        <img :src="item.iconSrc" :alt="item.value" />
      </div>

      <div class="text">{{ item.title }}</div>

      <input
        class="input"
        type="checkbox"
        :id="item.title"
        :value="item.value"
        :checked="item.selected"
        @change="handleChange"
      />
    </label>
  </div>
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
    handleChange(event) {
      this.$emit("change", {
        id: this.item.id,
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
    padding-left: 60px;
  }
}
</style>