<template>

  <div class="passportInfo">
    <div class="passportInfo__container container">

      <div class="passportInfo__content">

        <form id="form" @submit.prevent="onSubmit">
          <div class="passportInfo__block block">
            <div class="passportInfo__block_text">
              Паспортные данные
            </div>
            <EntryField v-for="passportInfo of passportInfo"
                        v-bind:key="passportInfo.name"
                        v-bind:type='passportInfo.type'
                        v-bind:name="passportInfo.name"
                        v-bind:class="passportInfo.class"
                        v-bind:options="passportInfo.options"
                        v-bind:required="passportInfo.required"
                        v-bind:title="passportInfo.label"/>
          </div>
        </form>
      </div>

    </div>
  </div>

</template>

<script>
import EntryField from "@/components/EntryField/EntryField";

export default {
  props: ['passportInfo'],
  components: {
    EntryField
  }
}
</script>

<style scoped>

</style>