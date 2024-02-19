<template>
  <div class="personalInfo">
    <div class="personalInfo__container container">

      <div class="personalInfo__content">

        <form id="form" @submit.prevent="onSubmit">
          <div class="personalInfo__block block">
            <div class="personalInfo__block_text">
              Личные данные
            </div>
            <EntryField v-for="personalInfo of personalInfo"
                        v-bind:key="personalInfo.name"
                        v-bind:type='personalInfo.type'
                        v-bind:name="personalInfo.name"
                        v-bind:class="personalInfo.class"
                        v-bind:options="personalInfo.options"
                        v-bind:required="personalInfo.required"
                        v-bind:title="personalInfo.label"/>
          </div>
        </form>
      </div>

      </div>

    </div>

</template>

<script>
import EntryField from "@/components/EntryField/EntryField";

export default {
  props: ['personalInfo'],
  components: {
    EntryField
  }
}

</script>

<style>

</style>