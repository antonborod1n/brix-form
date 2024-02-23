
<script>
import Footer from "./components/Footer.vue";
import Header from "./components/Header.vue";
import Input from "./components/Input.vue";
import Checkbox from "./components/Checkbox.vue";
import Radio from "./components/Radio.vue";
import NextStepButton from "./components/NextStepButton.vue";
import PreviousStepButton from "./components/PreviousStepButton.vue";

export default {
  components: {
    Input,
    Checkbox,
    Radio,
    NextStepButton,
    PreviousStepButton,
    Header,
    Footer,
  },
  data() {
    return {
      currentStep: 1,
      serice: [],
      formFields: [
        {
          id: 11,
          title: "Name",
          text: "John Carter",
          cssClass: "name",
          value: "",
        },
        {
          id: 12,
          title: "Email",
          text: "Email address",
          cssClass: "email",
          value: "",
        },
        {
          id: 13,
          title: "Phone Number",
          text: "(123) 456 - 7890",
          cssClass: "phone",
          value: "",
        },
        {
          id: 14,
          title: "Company",
          text: "Company name",
          cssClass: "company",
          value: "",
        },
      ],
      checkboxes: [
        {
          id: 1,
          iconSrc: "/img/icon-dev.svg",
          title: "Development",
          value: "development",
          selected: false,
        },
        {
          id: 2,
          iconSrc: "/img/icon-desing.svg",
          title: "Web Design",
          value: "design",
          selected: false,
        },
        {
          id: 3,
          iconSrc: "/img/icon-marketing.svg",
          title: "Marketing",
          value: "marketing",
          selected: false,
        },
        {
          id: 4,
          iconSrc: "/img/icon-other.svg",
          title: "Other",
          value: "other",
          selected: false,
        },
      ],
      radio: [
        {
          id: 1,
          title: "budget1",
          value: "5",
          text: "$5.000 - $10.000",
          selected: false,
        },
        {
          id: 2,
          title: "budget2",
          value: "10",
          text: "$10.000 - $20.000",
          selected: false,
        },
        {
          id: 3,
          title: "budget3",
          value: "20",
          text: "$20.000 - $50.000",
          selected: false,
        },
        {
          id: 4,
          title: "budget4",
          value: "50",
          text: "$50.000 +",
          selected: false,
        },
      ],
    };
  },
  methods: {
    handleInput(data) {
      const field = this.formFields.find((item) => item.id === data.id);
      if (field) {
        field.value = data.value;
      }
    },
    handleCheckboxChange(data) {
      const checkbox = this.checkboxes.find((item) => item.id === data.id);
      if (checkbox) {
        checkbox.selected = data.selected;
      }
    },
    handleRadioChange(data) {
      const radio = this.radio.find((item) => item.id === data.id);

      if (radio) {
        this.radio.forEach((item) => (item.selected = false));
        radio.selected = data.selected;
      }
    },
    nextStep() {
      this.currentStep++;
    },
    prevStep() {
      this.currentStep--;
    },
    submitForm() {
      // Сохранение данных в localStorage
      this.formFields.forEach((field) => {
        localStorage.setItem(field.title, field.value);
      });

      this.checkboxes.forEach((checkbox) => {
        localStorage.setItem(`checkbox_${checkbox.id}`, checkbox.selected);
      });

      const selectedRadio = this.radio.find((item) => item.selected);
      if (selectedRadio) {
        localStorage.setItem("selected_radio", selectedRadio.value);
      }

      console.log("Form submitted!");
    },
  },
};
</script>


<template>
  <Header />
  <main class="main">
    <section class="top">
      <div class="container">
        <div class="inner">
          <div class="box">
            <h1 class="title">Get a project quote</h1>
            <p class="text">
              Please fill the form below to receive a quote for your project.
              Feel free to add as much detail as needed.
            </p>
          </div>

          <section class="order">
            <div class="content">
              <div class="progress">
                <div class="item">
                  <span
                    class="num"
                    :class="{
                      active: currentStep,
                    }"
                    >1</span
                  >
                  <div
                    class="range"
                    :class="{
                      active: currentStep,
                      full: currentStep !== 1,
                    }"
                  ></div>
                </div>
                <div class="item">
                  <span
                    class="num"
                    :class="{
                      active: currentStep !== 1,
                    }"
                    >2</span
                  >
                  <div
                    class="range"
                    :class="{
                      active: currentStep === 2,
                      full: currentStep === 3 || currentStep === 4,
                    }"
                  ></div>
                </div>
                <div class="item">
                  <span
                    class="num"
                    :class="{
                      active: currentStep === 3 || currentStep === 4,
                    }"
                    >3</span
                  >
                  <div
                    class="range"
                    :class="{
                      active: currentStep === 3,
                      full: currentStep === 4,
                    }"
                  ></div>
                </div>
                <div class="item">
                  <span
                    class="num"
                    :class="{
                      active: currentStep === 4,
                    }"
                    >4</span
                  >
                </div>
              </div>

              <form class="form" action="#">
                <div class="step1" v-show="currentStep === 1">
                  <div class="top">
                    <h2 class="subtitle">Contact details</h2>
                    <p class="slogan">
                      Lorem ipsum dolor sit amet consectetur adipisc.
                    </p>
                  </div>

                  <div class="grid">
                    <Input
                      v-for="field in formFields"
                      :key="field.id"
                      :field="field"
                      @input="handleInput"
                    />
                  </div>
                </div>

                <div class="step2" v-show="currentStep === 2">
                  <div class="top">
                    <h2 class="subtitle">Our services</h2>
                    <p class="slogan">
                      Please select which service you are interested in.
                    </p>
                  </div>

                  <div class="grid">
                    <Checkbox
                      v-for="item in checkboxes"
                      :key="item.id"
                      :id="item.id"
                      :iconSrc="item.iconSrc"
                      :title="item.title"
                      :value="item.value"
                      :selected="item.selected"
                      @change="handleCheckboxChange"
                    />
                  </div>
                </div>

                <div class="step3" v-show="currentStep === 3">
                  <div class="top">
                    <h2 class="subtitle">What’s your project budget?</h2>
                    <p class="slogan">
                      Please select the project budget range you have in mind.
                    </p>
                  </div>

                  <div class="grid">
                    <Radio
                      v-for="item in radio"
                      :key="item.id"
                      :id="item.id"
                      :title="item.title"
                      :value="item.value"
                      :text="item.text"
                      :selected="item.selected"
                      @change="handleRadioChange"
                    />
                  </div>
                </div>

                <div class="step4" v-show="currentStep === 4">
                  <div class="top">
                    <img
                      class="img"
                      src="../public/img/submit-bg.svg"
                      alt="Форма отправленна"
                    />
                    <h2 class="subtitle">Submit your quote request</h2>
                    <p class="slogan">
                      Please review all the information you previously typed in
                      the past steps, and if all is okay, submit your message to
                      receive a project quote in 24 - 48 hours.
                    </p>
                  </div>
                  <button class="submit" @click="submitForm">Submit</button>
                </div>
              </form>
            </div>
            <div
              class="btns"
              :class="{
                one: currentStep === 1,
              }"
            >
              <PreviousStepButton
                class="btn prev"
                v-show="currentStep !== 1"
                @prev="prevStep"
              />
              <NextStepButton
                class="btn next"
                v-show="currentStep !== 4"
                @next="nextStep"
              />
            </div>
          </section>
        </div>
      </div>
    </section>
  </main>
  <Footer />
</template>

<style scoped lang="scss">
@import "./assets/styles/vars.scss";
.top {
  .inner {
    max-width: 698px;
    margin: 0 auto;
    padding: 56px 0 100px;
    @media (max-width: 1000px) {
      padding: 10px 0 20px;
    }
  }
  .box {
    max-width: 566px;
    margin: 0 auto 50px;
    @media (max-width: 1000px) {
      margin: 0 auto 25px;
    }
  }
  .title {
    @extend %dms-700;
    color: $black;
    text-align: center;
    font-size: 34px;
    line-height: 46px;
    margin-bottom: 12px;
    @media (max-width: 1000px) {
      font-size: 26px;
      line-height: 36px;
      margin-bottom: 6px;
    }
  }
  .text {
    @extend %dms-400;
    color: $grey;
    text-align: center;
    font-size: 18px;
    line-height: 30px;
    @media (max-width: 1000px) {
      font-size: 16px;
      line-height: 26px;
    }
  }
  .btns {
    display: flex;
    justify-content: space-between;
    align-items: center;
    &.one {
      justify-content: flex-end;
    }
  }
  .prev {
    @extend %dms-400;
    @extend %f-cc;
    width: 192px;
    height: 60px;
    color: $accent;
    font-size: 18px;
    line-height: 20px;
    border-radius: 66px;
    border: 1px solid $accent;
    background-color: transparent;
    cursor: pointer;
    transition: all 0.3s linear;
    &:hover {
      color: darken($color: $accent, $amount: 10%);
      box-shadow: 0px 3px 12px 0px rgba(74, 58, 255, 0.3);
    }
    @media (max-width: 1000px) {
      width: 165px;
      height: 41px;
    }
  }
  .next {
    @extend %btn-r;
    @extend %btn;
    @extend %dms-700;
    width: 165px;
    height: 60px;
    color: $white;
    font-size: 18px;
    line-height: 20px;
    @media (max-width: 1000px) {
      width: 130px;
      height: 41px;
    }
  }
}
.order {
  .progress {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 30px 30px;
    border-bottom: 1px solid $light-gray;
    margin-bottom: 64px;
    @media (max-width: 1000px) {
      justify-content: center;
      padding: 0 10px 25px 10px;
      margin-bottom: 25px;
      gap: 15px;
    }
    @media (max-width: 600px) {
      justify-content: center;
      gap: 5px;
    }
    @media (max-width: 350px) {
      flex-wrap: wrap;
    }
    .num {
      @extend %dms-400;
      @extend %f-cc;
      width: 34px;
      height: 34px;
      border-radius: 50%;
      color: $white;
      background-color: $white2;
      color: $grey;
      font-size: 16px;
      line-height: 23px;
    }
    .num.active {
      color: $white;
      background-color: $accent;
    }
    .range {
      position: relative;
      width: 100px;
      height: 6px;
      border-radius: 40px;
      background-color: $white2;
      @media (max-width: 600px) {
        width: 50px;
      }
      @media (max-width: 450px) {
        width: 25px;
      }
    }
    .range.active {
      &::after {
        position: absolute;
        z-index: 1;
        content: "";
        width: 50%;
        height: 6px;
        border-radius: 40px;
        background-color: $accent;
      }
    }
    .range.full {
      &::after {
        position: absolute;
        z-index: 1;
        content: "";
        width: 100%;
        height: 6px;
        border-radius: 40px;
        background-color: $accent;
      }
    }
  }
  .item {
    display: flex;
    align-items: center;
    gap: 15px;
    @media (max-width: 600px) {
      gap: 5px;
    }
  }
  .content {
    padding: 32px 55px 80px 46px;
    border-radius: 34px;
    border: 1px solid $white2;
    background-color: $white;
    box-shadow: 0px 5px 16px 0px rgba(8, 15, 52, 0.06);
    margin-bottom: 32px;
    @media (max-width: 1000px) {
      padding: 16px 27px 40px 24px;
      margin-bottom: 16px;
    }
  }
  .subtitle {
    @extend %dms-700;
    color: $black;
    font-size: 24px;
    line-height: 35px;
    margin-bottom: 7px;
    @media (max-width: 1000px) {
      font-size: 20px;
      line-height: 30px;
    }
  }
  .slogan {
    @extend %dms-400;
    color: $grey;
    font-size: 18px;
    line-height: 30px;
    margin-bottom: 40px;
    @media (max-width: 1000px) {
      ffont-size: 16px;
      line-height: 24px;
      margin-bottom: 20px;
    }
  }
  .form {
    .grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      grid-template-rows: repeat(2, 1fr);
      gap: 44px 28px;

      @media (max-width: 678px) {
        grid-template-columns: repeat(1, 1fr);
        grid-template-rows: repeat(4, 1fr);
        gap: 20px;
      }
    }
  }
}
.step4 {
  text-align: center;
  img {
    margin: 0 auto 18px;
  }
  .submit {
    @extend %btn-r;
    @extend %btn;
    padding: 20px 30px 20px 30px;
    margin: 0 auto;
  }
}
</style>

