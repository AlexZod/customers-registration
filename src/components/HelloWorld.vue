<template>
  <div class="hello">

<form @submit.prevent="submit">
  <div class="form-group" :class="{ 'form-group--error': $v.lastName.$error }">
    <label class="form__label">Фамилия</label>
    <input class="form__input" v-model.trim="$v.lastName.$model"/>
    <div class="error" v-if="submitStatus === 'ERROR'">Поле необходимо для заполнения</div>
  </div>
  
  <div class="form-group" :class="{ 'form-group--error': $v.firstName.$error }">
    <label class="form__label">Имя</label>
    <input class="form__input" v-model.trim="$v.firstName.$model"/>
        <div class="error" v-if="submitStatus === 'ERROR'">Поле необходимо для заполнения</div>
  </div>

  <div class="form-group" :class="{ 'form-group--error': $v.patronymic.$error }">
    <label class="form__label">Отчество</label>
    <input class="form__input" v-model.trim="$v.patronymic.$model"/>
  </div>
  
  <button class="button" type="submit" :disabled="submitStatus === 'PENDING'">Submit!</button>
  <p class="typo__p" v-if="submitStatus === 'OK'">Thanks for your submission!</p>
  <p class="typo__p error" v-if="submitStatus === 'ERROR'">Пожалуйста, заполните все необходимые поля.</p>
  <p class="typo__p" v-if="submitStatus === 'PENDING'">Sending...</p>
</form>

</div>
</template>

<script>
import { required} from 'vuelidate/lib/validators'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      firstName: '',
      lastName: '',
      patronymic: '',
      age: 0,
      submitStatus: null
    }
  },
  validations: {
    firstName: {
      required,
    },
    lastName: {
      required,
    },
    patronymic : {

    }
  },
  methods: {
    submit() {
      console.log('submit!')
      this.$v.$touch()
      if (this.$v.$invalid) {
        this.submitStatus = 'ERROR'
      } else {
        // do your submit logic here
        this.submitStatus = 'PENDING'
        setTimeout(() => {
          this.submitStatus = 'OK'
        }, 500)
      }
    }
  }
}
</script>

<style scoped>
  .form__label {
    display: block;
  }
  .error {
    color: red;
    font-size: 12px;
  }
</style>
