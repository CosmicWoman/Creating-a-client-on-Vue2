<template>
  <div class="blocks">
    <div class="blocks -container container">

      <div class="blocks -content">

        <div class="blocks -title">Данные нового клиента</div>


        <form v-on:submit.prevent="handleSubmit()">
          <div class="blocks -block">
            <div class="personalInfo -block block">
              <div class="personalInfo -block_text">
                Личные данные
              </div>
              <div class="block_field">

                <div class="typeInput">
                  <div class="typeInput -title">{{ personalData[0].title }}
                    <p v-if="v$.formClient.lastName.required">*</p>
                  </div>

                  <input type="text"
                         id='last-name'
                         class="inputStyle"
                         v-bind:class="{invalid: v$.formClient.lastName.$error}"
                         v-model="formClient.lastName"
                  />

                  <biv class="error-message" v-if="v$.formClient.lastName.$error">{{ formClient.errorText }}</biv>
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ personalData[1].title }}
                    <p v-if="v$.formClient.firstName.required">*</p>
                  </div>

                  <input type="text"
                         id='first-name'
                         class="inputStyle"
                         v-bind:class="{invalid: v$.formClient.lastName.$error}"
                         v-model="formClient.firstName"
                  />

                  <biv class="error-message" v-if="v$.formClient.firstName.$error">{{ formClient.errorText }}</biv>
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ personalData[2].title }}
                  </div>

                  <input type="text"
                         id='surname'
                         class="inputStyle"
                         v-model="formClient.surname"
                  />

                </div>
                <div class="typeInputDate">
                  <div class="typeInput -title">{{ personalData[3].title }}
                    <p v-if="v$.formClient.birthday.required">*</p>
                  </div>
                  <input type="date"
                         id="birthday"
                         class="inputStyle"
                         v-bind:class="{invalid: v$.formClient.lastName.$error}"
                         v-model="formClient.birthday"
                  />
                  <biv class="error-message" v-if="v$.formClient.birthday.$error">{{ formClient.errorText }}</biv>
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ personalData[4].title }}
                    <p v-if="v$.formClient.phone.required">*</p>
                  </div>

                  <input type="text"
                         id='phone'
                         class="inputStyle"
                         v-bind:class="{invalid: v$.formClient.lastName.$error}"
                         v-model="formClient.phone"
                         oninput="this.value = this.value.replace(/[^0-9]/g, '')"
                  />

                  <biv class="error-message" v-if="v$.formClient.phone.$error">{{ formClient.errorNum }}</biv>
                </div>
                <div class="typeRadio">
                  <div class="typeInput -title">{{ personalData[5].title }}
                  </div>
                  <div class="typeRadio radioBlock">
                    <div class="radioBlock male">
                      <input type="radio"
                             id='male'
                             class='gender'
                             value="male"
                             v-model="formClient.gender"
                      />
                      <label for="male" class="radio -title">
                        М
                      </label>
                    </div>

                    <div class="radioBlock female">
                      <input type="radio"
                             id="female"
                             class='gender'
                             value="female"
                             v-model="formClient.gender"
                      />
                      <label for="female" class="radio -title">
                        Ж
                      </label>
                    </div>

                  </div>
                </div>
                <div class="typeMultiSel">
                  <div class="typeInput -title">{{ personalData[6].title }}
                    <p v-if="v$.formClient.groupClient.required">*</p>
                  </div>
                  <select id='groupClient'
                          class="multiSelStyle"
                          v-bind:class="{invalid: v$.formClient.lastName.$error}"
                          :size="personalData[6].options.length"
                          v-model="formClient.groupClient"
                          multiple>
                    <option v-for="option in personalData[6].options"
                            :key="option"
                            :value="option">
                      {{ option }}
                    </option>
                  </select>
                  <biv class="error-message" v-if="v$.formClient.groupClient.$error">{{ formClient.errorText }}</biv>

                </div>
                <div class="typeSelector">
                  <div class="typeInput -title">{{ personalData[7].title }}
                  </div>
                  <select id='doctor'
                          class="inputStyle"
                          v-model="formClient.doctor">
                    <option v-for="option in personalData[7].options"
                            :key="option"
                            :value="option">
                      {{ option }}
                    </option>
                  </select>
                </div>
                <div class="typeCheckbox">
                  <div class="typeCheckbox -title">{{ personalData[8].title }}
                    <input type="checkbox"
                           id='sms'
                           class="checkedStyle"
                           v-model="formClient.notification"
                    />
                  </div>

                </div>

              </div>
            </div>

            <div class="addressInfo -block block">
              <div class="addressInfo -block_text">
                Адрес клиента
              </div>
              <div class="block_field">

                <div class="typeInput">
                  <div class="typeInput -title">{{ addressInfo[0].title }}
                  </div>

                  <input type="text"
                         id='index'
                         class="inputStyle"
                         v-model.number="formClient.indexNum"
                  />

                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ addressInfo[1].title }}
                  </div>
                  <input type="text"
                         id='country'
                         class="inputStyle"
                         v-model="formClient.country"
                  />
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ addressInfo[2].title }}
                  </div>
                  <input type="text"
                         id='region'
                         class="inputStyle"
                         v-model="formClient.region"
                  />
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ addressInfo[3].title }}
                    <p v-if="v$.formClient.city.required">*</p>
                  </div>
                  <input type="text"
                         id='city'
                         class="inputStyle"
                         v-bind:class="{invalid: v$.formClient.lastName.$error}"
                         v-model="formClient.city"
                  />
                  <biv class="error-message" v-if="v$.formClient.city.$error">{{ formClient.errorText }}</biv>

                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ addressInfo[4].title }}
                  </div>
                  <input type="text"
                         id='street'
                         class="inputStyle"
                         v-model="formClient.street"
                  />
                </div>
                <div class="typeInputNum">
                  <div class="typeInput -title">{{ addressInfo[5].title }}
                  </div>
                  <input type="text"
                         id="house"
                         class="inputStyle"
                         v-model.number="formClient.house"
                  />
                </div>

              </div>
            </div>

            <div class="passportInfo -block block">
              <div class="passportInfo -block_text">
                Паспортные данные
              </div>
              <div class="block_field">

                <div class="typeSelector">
                  <div class="typeInput -title">{{ passportInfo[0].title }}
                    <p v-if="v$.formClient.typeDocument.required">*</p>
                  </div>
                  <select id='document'
                          class="inputStyle"
                          v-bind:class="{invalid: v$.formClient.lastName.$error}"
                          v-model="formClient.typeDocument">
                    <option v-for="option in passportInfo[0].options"
                            :key="option"
                            :value="option">
                      {{ option }}
                    </option>
                  </select>
                  <biv class="error-message" v-if="v$.formClient.typeDocument.$error">{{ formClient.errorText }}</biv>

                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ passportInfo[1].title }}

                  </div>

                  <input type="text"
                         id='series'
                         class="inputStyle"
                         v-model.number="formClient.series"
                  />
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ passportInfo[2].title }}
                  </div>

                  <input type="text"
                         id='numberPassport'
                         class="inputStyle"
                         v-model.number="formClient.number"
                  />
                </div>
                <div class="typeInput">
                  <div class="typeInput -title">{{ passportInfo[3].title }}
                  </div>

                  <input type="text"
                         id='issued'
                         class="inputStyle"
                         v-model="formClient.issued"
                  />

                </div>
                <div class="typeInputDate">
                  <div class="typeInput -title">{{ passportInfo[4].title }}
                    <p v-if="v$.formClient.dateOfIssue.required">*</p>
                  </div>
                  <input type="date"
                         id="dateIssues"
                         class="inputStyle"
                         v-bind:class="{invalid: v$.formClient.lastName.$error}"
                         v-model="formClient.dateOfIssue"
                  />
                  <biv class="error-message" v-if="v$.formClient.dateOfIssue.$error">{{ formClient.errorText }}</biv>
                </div>

              </div>
            </div>

          </div>
          <div class="blocks -btn">
            <button type="submit">
              Создать клиента
            </button>
          </div>
        </form>

        <div class="creatingClient" ref="creatingClient">
          <div class="creatingClient -block">
            <p class="text">Новый клиент успешно создан!</p>
            <button class="btn"  type="submit" v-on:click="closeBlock">Выход</button>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import {required} from "vuelidate/lib/validators";
import {useVuelidate} from "@vuelidate/core";

export default {
  setup() {
    return {
      v$: useVuelidate()
    }
  },

  data() {
    return {
      formClient: {
        submitted: false,
        lastName: '',
        firstName: '',
        surname: '',
        birthday: '',
        phone: '',
        gender: '',
        groupClient: [],
        doctor: '',
        notification: false,
        indexNum: '',
        country: '',
        region: '',
        city: '',
        street: '',
        house: '',
        documentType: '',
        series: '',
        number: '',
        issued: '',
        dateOfIssue: '',
        errorText: 'Поле обязательное для заполнения',
        errorNum: 'Номер начинается с 7, состоит из 11 цифр'
      },
      personalData: [
        {title: 'Фамилия', name: 'lastName', class: 'lastName', type: 'input', required: true},
        {title: 'Имя', name: 'firstName', class: 'name', type: 'input', required: true},
        {title: 'Отчество', name: 'surname', class: 'Surname', type: 'input'},
        {title: 'Дата рождения', name: 'birthday', class: 'dateOfBirth', type: 'inputDate', required: true},
        {title: 'Телефон', name: 'phone', class: 'phoneNumber', type: 'inputNum'},
        {title: 'Пол', name: 'gender', class: 'gender', type: 'radio'},
        {
          title: 'Группа клиентов', name: 'groupClient', class: 'clientGroup', type: 'multSelector',
          options: ['VIP', 'Проблемные', 'ОМС'], required: true
        },
        {
          title: 'Лечащий врач', name: 'doctor', class: 'doctor', type: 'selector',
          options: ['Иванов', 'Захаров', 'Чернышев']
        },
        {title: 'Не отправлять СМС', name: 'notification', class: 'dontSendSMS', type: 'checkbox'}
      ],

      addressInfo: [
        {title: 'Индекс', name: 'indexNum', class: 'indexNum', type: 'input'},
        {title: 'Страна', name: 'country', class: 'country', type: 'input'},
        {title: 'Область', name: 'region', class: 'region', type: 'input'},
        {title: 'Город', name: 'city', class: 'city', type: 'input', required: true},
        {title: 'Улица', name: 'street', class: 'street', type: 'input'},
        {title: 'Дом', name: 'house', class: 'house', type: 'input'}
      ],

      passportInfo: [
        {
          title: 'Тип документа', name: 'documentType', class: 'documentType', type: 'selector',
          options: ['Паспорт', 'Свидетельство о рождении', 'Водительское удостоверение'], required: true
        },
        {title: 'Серия', name: 'series', class: 'series', type: 'input'},
        {title: 'Номер', name: 'number', class: 'number', type: 'input'},
        {title: 'Выдан', name: 'issued', class: 'issued', type: 'input'},
        {title: 'Дата выдачи', name: 'dateOfIssue', class: 'dateOfIssue', type: 'inputDate', required: true}
      ]

    }
  },

  validations() {
    return {
      formClient: {
        lastName: {required},
        firstName: {required},
        birthday: {required},
        phone: {
          length(value) {
            return value.length === 11 && value[0] === '7'
          }
        },
        groupClient: {required},
        city: {required},
        typeDocument: {required},
        dateOfIssue: {required},
      }
    }
  },

  methods: {
    handleSubmit() {
      this.formClient.submitted = true;
      this.v$.formClient.$touch();
      if (this.v$.formClient.$invalid) {
        return '';
      } else {
        const elem = this.$refs.creatingClient
        elem.style.display = 'block'
      }
    },
    closeBlock(){
      const elem = this.$refs.creatingClient
      elem.style.display = 'none'
    }
  }
}
</script>

<style scoped lang="sass" src='../style/newClient.sass'/>
<style scoped lang="sass" src='../style/styleBlockInfo.sass'/>
<style scoped lang="sass" src='../style/inputStyle.sass'/>