<template>
  <section class="form">
    <div class="container">
      <h2>Отправь форму</h2>
      <form action="/" name="site-form">
        <div class="form__top">
          <label>
            <input
                type="text"
                name="form-name"
                v-model="inputName"
                @focusin="labelChange"
                @focusout="labelChange"
                placeholder="Text">
            <span>Имя</span>
          </label>
          <label>
            <input
                type="text"
                name="form-phone"
                v-model="inputPhone"
                @focusin="labelChange"
                @focusout="labelChange"
                data-inputmask="'mask': '+7 (999)-999-99-99'"
                inputmode="text">
            <span>Телефон</span>
          </label>
        </div>
        <div class="form__bottom">
          <div>
            <input id="agreement" type="checkbox" name="form-agreement">
            <label for="agreement">Я соглашаюсь</label>
          </div>
          <button type="button" class="blue-button">Отправить</button>
        </div>
      </form>
    </div>
  </section>
</template>

<script>

  import Inputmask from "inputmask";

  export default {
    name: "site-form",
    data() {
      return {
        inputName: "",
        inputPhone: "",
        inputAgreement: "",
      }
    },
    mounted() {
      let phoneElement = document.querySelector('[name="form-phone"]');
      Inputmask().mask(phoneElement);
    },
    methods: {
      labelChange(event) {
        event.target.parentElement.classList.toggle('active');
      }
    }
  }
</script>