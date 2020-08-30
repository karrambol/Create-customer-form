<template>
  <div class="form-group" :class="{ 'form-group--error': error }">
    <label class="form__label">{{ label }}</label>
    <input class="form__input" v-model.trim="model" />
    <div class="error" v-if="!numeric">
      Поле должно содержать тольцо цифры
    </div>
    <div class="error" v-if="!required">
      Поле необходимо заполнить
    </div>
  </div>
</template>
<script>
export default {
  props: {
    field: { type: Object, reguired: true },
    label: { type: String, required: true }
  },
  data () {
    return {
      error: this.field.$error,
      model: this.field.$model,
      numeric: this.field.numeric,
      required: this.field.required
    }
  }
}
</script>
