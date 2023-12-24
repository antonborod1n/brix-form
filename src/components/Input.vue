<template>
  <label class="label" :for="field.title">
    <div class="title">{{ field.title }}</div>
    <input
      class="input"
      :class="field.cssClass"
      :type="field.type"
      :value="field.value"
      :placeholder="field.text"
      @input="handleInput"
    />
  </label>
</template>
  
  <script>
export default {
  props: {
    field: {
      type: Object,
      required: true,
    },
  },
  methods: {
    handleInput(event) {
      this.$emit("input", {
        id: this.field.id,
        value: event.target.value,
      });
    },
  },
};
</script>

<style scoped lang="scss">
@import "../assets/styles/vars";
.step1 {
  .title {
    @extend %dms-500;
    font-size: 18px;
    line-height: 20px;
    margin-bottom: 18px;
    color: $black;
  }
  .input {
    @extend %dms-400;
    width: 284px;
    height: 66px;
    padding: 22px 55px 22px 22px;
    color: $grey;
    font-size: 18px;
    line-height: 20px;
    border-radius: 46px;
    border: 1px solid $white2;
    background-color: $white;
    box-shadow: 0px 2px 6px 0px rgba(19, 18, 66, 0.07);
    background-repeat: no-repeat;
    background-position: right 20px center;
    @media (max-width: 1000px) {
      font-size: 16px;
    }
    @media (max-width: 600px) {
      width: 100%;
      height: 50px;
      padding: 15px 55px 15px 15px;
    }
    &.name {
      background-image: url("../../public/img/icon-user.svg");
    }
    &.email {
      background-image: url("../../public/img/icon-email.svg");
    }
    &.phone {
      background-image: url("../../public/img/icon-phone.svg");
    }
    &.company {
      background-image: url("../../public/img/icon-company.svg");
    }
  }
}
</style>
  