<template>
  <div class="personalInfo">
    <div class="personalInfo -container container">

      <div class="personalInfo -content">

          <div class="personalInfo -block block">
            <div class="personalInfo -block_text">
              Личные данные
            </div>
            <div class="block_field">
              <EntryField v-for="personalInfo of personalInfo"
                          v-bind:key="personalInfo.name"
                          v-bind:type='personalInfo.type'
                          v-bind:name="personalInfo.name"
                          v-bind:class="personalInfo.class"
                          v-bind:options="personalInfo.options"
                          v-bind:required="personalInfo.required"
                          v-bind:title="personalInfo.title"
                          v-bind:v="v$"/>
            </div>

          </div>
      </div>

      </div>

    </div>

</template>

<script>
import EntryField from "@/components/failed_implementation/EntryField/EntryField";
import {required} from "vuelidate/lib/validators";
import { useVuelidate } from '@vuelidate/core'

export default {
  props: ['personalInfo'],
  setup() {
    return {v$: useVuelidate()}
  },

  components: {
    EntryField
  },

  validations() {
    return {
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
  }
}

</script>

<style scoped lang="sass" src="../../style/styleBlockInfo.sass">

</style>