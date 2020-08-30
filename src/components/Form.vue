<template>
  <div class="form">
    <h1>Создать клиента</h1>

    <div class="form-group" :class="{ 'form-group--error': $v.surname.$error }">
      <label class="form__label">Фамилия*</label>
      <input class="form__input" v-model.trim="$v.surname.$model" />
      <div class="error" v-if="!$v.surname.required && $v.surname.$error">
        Поле необходимо заполнить
      </div>
    </div>

    <div class="form-group" :class="{ 'form-group--error': $v.name.$error }">
      <label class="form__label">Имя*</label>
      <input class="form__input" v-model.trim="$v.name.$model" />
      <div class="error" v-if="!$v.name.required && $v.name.$error">
        Поле необходимо заполнить
      </div>
    </div>

    <div class="form-group" :class="{ 'form-group--error': $v.midName.$error }">
      <label class="form__label">Отчество</label>
      <input class="form__input" v-model.trim="$v.midName.$model" />
    </div>

    <div
      class="form-group"
      :class="{ 'form-group--error': $v.dateOfBirth.$error }"
    >
      <label class="form__label">Дата рождения*</label>
      <input
        type="date"
        class="form__input"
        v-model.trim="$v.dateOfBirth.$model"
      />
      <div
        class="error"
        v-if="!$v.dateOfBirth.required && $v.dateOfBirth.$error"
      >
        Поле необходимо заполнить
      </div>
    </div>

    <div
      class="form-group"
      :class="{ 'form-group--error': $v.telephone.$error }"
    >
      <label class="form__label">Номер телефона*</label>
      <input
        type="tel"
        class="form__input"
        v-model.trim="$v.telephone.$model"
      />
      <div class="error" v-if="!$v.telephone.required && $v.telephone.$error">
        Поле необходимо заполнить
      </div>
      <div class="error" v-if="!$v.telephone.length && $v.telephone.$dirty">
        Поле должно содержать 11 знаков
      </div>
      <div class="error" v-if="!$v.telephone.numeric && $v.telephone.$dirty">
        Поле должно содержать только цифры
      </div>
    </div>

    <div class="form-group" :class="{ 'form-group--error': $v.sex.$error }">
      <label class="form__label">Пол</label>
      <select name="sex" id="sex" v-model="$v.sex.$model">
        <option>Не задан</option>
        <option>Мужской</option>
        <option>Женский</option>
      </select>
    </div>

    <div
      class="form-group"
      :class="{ 'form-group--error': $v.customerGroup.$error }"
    >
      <label class="form__label">Группа клиентов*</label>
      <select
        class="form__select"
        name="customerGroup"
        id="customerGroup"
        v-model="$v.customerGroup.$model"
        multiple
      >
        <option>VIP</option>
        <option>Проблемные</option>
        <option>ОМС</option>
      </select>
      <div
        class="error"
        v-if="!$v.customerGroup.required && $v.customerGroup.$error"
      >
        Поле необходимо заполнить
      </div>
    </div>

    <div class="form-group" :class="{ 'form-group--error': $v.doctor.$error }">
      <label class="form__label">Лечащий врач</label>
      <select
        class="form__select"
        name="doctor"
        id="doctor"
        v-model="$v.doctor.$model"
      >
        <option>Иванов</option>
        <option>Захаров</option>
        <option>Чернышева</option>
      </select>
    </div>

    <div
      class="form-group"
      :class="{ 'form-group--error': $v.disableSMS.$error }"
    >
      <input
        type="checkbox"
        class="form__input"
        v-model="$v.disableSMS.$model"
        id="SMS"
      />
      <label class="form__label" for="SMS">Не отправлять СМС</label>
    </div>

    <fieldset>
      <legend>Адрес</legend>
      <div
        class="form-group"
        :class="{ 'form-group--error': $v.adress.postalCode.$error }"
      >
        <label class="form__label">Индекс</label>
        <input class="form__input" v-model.trim="$v.adress.postalCode.$model" />
        <div class="error" v-if="!$v.adress.postalCode.numeric">
          Поле должно содержать тольцо цифры
        </div>
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.adress.country.$error }"
      >
        <label class="form__label">Страна</label>
        <input class="form__input" v-model.trim="$v.adress.country.$model" />
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.adress.region.$error }"
      >
        <label class="form__label">Область</label>
        <input class="form__input" v-model.trim="$v.adress.region.$model" />
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.adress.city.$error }"
      >
        <label class="form__label">Город*</label>
        <input class="form__input" v-model.trim="$v.adress.city.$model" />
        <div
          class="error"
          v-if="!$v.adress.city.required && $v.adress.city.$error"
        >
          Поле необходимо заполнить
        </div>
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.adress.street.$error }"
      >
        <label class="form__label">Улица</label>
        <input class="form__input" v-model.trim="$v.adress.street.$model" />
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.adress.house.$error }"
      >
        <label class="form__label">Дом</label>
        <input class="form__input" v-model.trim="$v.adress.house.$model" />
      </div>
    </fieldset>

    <fieldset>
      <legend>Документ</legend>
      <div
        class="form-group"
        :class="{ 'form-group--error': $v.document.type.$error }"
      >
        <label class="form__label">Тип документа*</label>
        <select
          name="document-type"
          id="document-type"
          v-model="$v.document.type.$model"
        >
          <option>Паспорт</option>
          <option>Свидетельство о рождении</option>
          <option>Вод. удостоверение</option>
        </select>
        <div
          class="error"
          v-if="!$v.document.type.required && $v.document.type.$error"
        >
          Поле необходимо заполнить
        </div>
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.document.batch.$error }"
      >
        <label class="form__label">Серия</label>
        <input class="form__input" v-model.trim="$v.document.batch.$model" />
      </div>
      <div
        class="form-group"
        :class="{ 'form-group--error': $v.document.number.$error }"
      >
        <label class="form__label">Номер</label>
        <input class="form__input" v-model.trim="$v.document.number.$model" />
      </div>
      <div
        class="form-group"
        :class="{ 'form-group--error': $v.document.issuer.$error }"
      >
        <label class="form__label">Кем выдан</label>
        <input class="form__input" v-model.trim="$v.document.issuer.$model" />
      </div>

      <div
        class="form-group"
        :class="{ 'form-group--error': $v.document.issueDate.$error }"
      >
        <label class="form__label">Дата рождения*</label>
        <input
          type="date"
          class="form__input"
          v-model.trim="$v.document.issueDate.$model"
        />
        <div
          class="error"
          v-if="!$v.document.issueDate.required && $v.document.issueDate.$error"
        >
          Поле необходимо заполнить
        </div>
      </div>
    </fieldset>

    <div class="form-group button-wraper">
      <p v-if="submitStatus === 'OK'">Клиент создан</p>
      <p class="error" v-if="submitStatus === 'ERROR'">
        Форма заполнена не корректно
      </p>
      <button class="submit" v-on:click="submit()">Создать</button>
    </div>
  </div>
</template>

<script>
import {
  required,
  minLength,
  maxLength,
  numeric,
  and
} from 'vuelidate/lib/validators'

export default {
  name: 'Form',
  data () {
    return {
      submitStatus: undefined,
      surname: '',
      name: '',
      midName: '',
      dateOfBirth: '',
      telephone: '7',
      sex: 'Не задан',
      customerGroup: [],
      doctor: '',
      disableSMS: false,
      adress: {
        postalCode: '',
        country: '',
        region: '',
        city: '',
        street: '',
        house: ''
      },
      document: {
        type: '',
        batch: '',
        number: '',
        issuer: '',
        street: '',
        issueDate: ''
      }
    }
  },
  validations: {
    surname: { required },
    name: { required },
    midName: {},
    dateOfBirth: { required },
    telephone: {
      required,
      length: and(minLength(11), maxLength(11)),
      numeric
    },
    sex: {},
    customerGroup: { required },
    doctor: {},
    disableSMS: {},
    adress: {
      postalCode: { numeric },
      country: {},
      region: {},
      city: { required },
      street: {},
      house: {}
    },
    document: {
      type: { required },
      batch: {},
      number: {},
      issuer: {},
      street: {},
      issueDate: { required }
    }
  },
  computed: {
    lol () {
      console.log(this.sex)
      return this.sex
    }
  },
  methods: {
    touch (field) {
      return function (event) {
        field.$model = event.target.value
        field.$touch()
      }
    },
    submit () {
      this.$v.$touch()
      if (this.$v.$invalid) {
        this.submitStatus = 'ERROR'
      } else {
        this.submitStatus = 'OK'
      }
      console.log(this.submitStatus)
      console.dir(this.$v)
    }
  }
}
</script>

<style scoped lang="scss">
.form {
  --error: #cc2b2b;
  font-size: 18px;
  // max-width: 400px;
  width: fit-content;
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: flex-end;
  align-items: flex-start;
  margin: 0 auto;
  h1 {
    font-size: 24px;
    align-self: center;
    margin: 0 5px;
  }
  .form-group {
    margin: 5px;
    display: block;
    // width: 100%;

    label {
      display: block;
      text-align: left;
      width: fit-content;
    }
    input[type='checkbox'],
    input[type='checkbox'] + label {
      display: inline-block;
      &:hover {
        cursor: pointer;
      }
    }
    input[type='checkbox'] {
      width: 20px;
      height: 20px;
      vertical-align: text-bottom;
    }
    input[type='checkbox'] + label {
      margin-left: 5px;
    }
    input,
    select {
      display: block;
      border: 1px solid black;
      border-radius: 3px;
      outline: var(--error);
      margin: 0;
      max-width: 175px;
      width: calc(100vw - 15px);
    }
    input {
      font-size: 16px;
    }
    select {
      font-size: 14px;
      &:not([multiple]):hover,
      option:hover {
        cursor: pointer;
      }
      option:nth-child(odd) {
        background-color: #eee;
      }
    }

    .error {
      text-align: left;
      display: block;
      font-size: 13px;
      color: var(--error);
    }
  }
  fieldset {
    margin: 5px;
    legend {
      text-align: start;
    }
  }
  .button-wraper {
    width: calc(100% - 10px);
    p {
      font-size: 14px;
      margin: 5px 0;
      text-align: center;
    }
    p.error {
      color: var(--error);
    }
    button.submit {
      margin: 5px;
      align-self: center;
      height: 25px;
      max-width: 150px;
      width: calc(100vw - 20px);
      cursor: pointer;
    }
  }
}

.form-group.form-group--error {
  label {
    color: var(--error);
  }
  input,
  select {
    border-color: var(--error);
  }
}
</style>
