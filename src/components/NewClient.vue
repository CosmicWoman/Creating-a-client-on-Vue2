<template>
  <PersonalInfo v-bind:personal-info="personalData"/>
</template>

<script>
import {required} from "vuelidate/lib/validators";
import PersonalInfo from "@/components/PersonalInfo";

export default {
  data() {
    return {
      formPersonalData: {
        lastName: '',
        firstName: '',
        surname: '',
        birthday: '',
        phone: '7',
        gender: '',
        groupClient: [],
        doctor: '',
        notification: ''
      },
      personalData: [
        {label: 'Фамилия', name: 'lastName', class: 'lastName', type: 'input', required: true},
        {label: 'Имя', name: 'firstName', class: 'name', type: 'input', required: true},
        {label: 'Отчество', name: 'surname', class: 'Surname', type: 'input'},
        {label: 'Дата рождения', name: 'birthday', class: 'dateOfBirth', type: 'inputDate', required: true},
        {label: 'Телефон', name: 'phone', class: 'phoneNumber', type: 'inputNum'},
        {label: 'Пол', name: 'gender', class: 'gender', type: 'radio'},
        {
          label: 'Группа клиентов', name: 'groupClient', class: 'clientGroup', type: 'multSelect',
          options: ['VIP', 'Проблемные', 'ОМС'], required: true
        },
        {
          label: 'Лечащий врач', name: 'doctor', class: 'doctor', type: 'selector',
          options: ['Иванов', 'Захаров', 'Чернышев']
        },
        {label: 'Не отправлять СМС', name: 'notification', class: 'dontSendSMS', type: 'checkbox'}
      ]

    }
  },

  validations: {
    formPersonalData: {
      lastName: {required},
      firstName: {required},
      birthday: {required},
      phone: {
        length(value) {
          return value.length === 11 && value[0] === '7'
        }
      },
      groupClient: {required}
    }
  },
  components:{
    PersonalInfo
  }
}
</script>

<style scoped>

</style>