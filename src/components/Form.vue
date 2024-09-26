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
                value=""
                @focusin="labelChange"
                @focusout="prepareField"
                placeholder="Text">
            <span>Имя</span>
          </label>
          <label>
            <input
                type="text"
                name="form-phone"
                value=""
                @focusin="labelChange"
                @focusout="prepareField"
                data-inputmask="'mask': '+7 (999)-999-99-99'"
                inputmode="text">
            <span>Телефон</span>
          </label>
        </div>
        <div class="form__bottom">
          <div>
            <input id="agreement" type="checkbox" name="form-agreement" value="Y">
            <label for="agreement">Я соглашаюсь</label>
          </div>
          <button type="button" @click="prepareForm" class="blue-button">Отправить</button>
        </div>
      </form>
    </div>
  </section>
</template>

<script>

  import Inputmask from "inputmask";

  export default {
    name: "site-form",
    mounted() {
      let phoneElement = document.querySelector('[name="form-phone"]');
      Inputmask().mask(phoneElement);
    },
    methods: {
      labelChange(event) {
        event.target.parentElement.classList.toggle('active');
      },
      toggleClasses(event, addClass = '', removeClass = '') {
        event.target.classList.add(addClass);
        event.target.parentElement.classList.add(addClass);
        event.target.classList.remove(removeClass);
        event.target.parentElement.classList.remove(removeClass);
      },
      addErrorElement(event, text = '') {
        let div = document.createElement('div');

        div.classList.add('form__error-element');
        div.innerText = text;

        event.target.parentElement.append(div);
      },
      removeErrorElement(event) {
        let div = event.target.parentElement.querySelector('.form__error-element')

        if(div) {
          div.remove();
        }
      },
      checkField(event, match, classError = '', classGood = '', text = '') {
        let matches = event.target.value.match(match);

        if (!matches) {
          this.toggleClasses(event, classError, classGood);
          this.addErrorElement(event, text);
        } else {
          this.toggleClasses(event, classGood, classError);
          this.removeErrorElement(event);
        }
      },
      prepareField(event) {
        this.labelChange(event);

        let classError = 'error',
            classGood = 'good';

        if (
            event.target.value.length > 0
            || (!event.target.classList.contains(classError) || !event.target.classList.contains(classGood))
        ) {
          if (event.target.name === 'form-phone') {
            this.checkField(event, /^\+7\s\(([0-9]){3}\)-([0-9]){3}(-([0-9]){2}){2}$/, classError, classGood, 'Некорректный номер');
          }

          if (event.target.name === 'form-name') {
            this.checkField(event, /^([A-ЯЁ])+([а-яё])+(\s)*([A-ЯЁ][а-яё])*$/, classError, classGood, 'Некорректное имя');
          }
        }
      },
      sendPost(data, url = '/') {
        fetch(url).then((response) => {
          console.log(response);
        });
      },
      prepareForm() {
        let form = document.querySelector('form'),
            formData = new FormData(form),
            countFields = 0;

        for (let pair of formData.entries()) {
          if (pair[1].length > 0) {
            countFields += 1;
          }
        }

        if (countFields === 3 && document.querySelectorAll('.good').length >= 4) {
          let params = new URLSearchParams(formData).toString();
          this.sendPost(formData, form.action + '?' + params);
        }
      }
    },
  }
</script>