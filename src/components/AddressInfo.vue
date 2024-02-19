<template>

  <div class="addressInfo">
    <div class="addressInfo__container container">

      <div class="addressInfo__content">

        <form id="form" @submit.prevent="onSubmit">
          <div class="addressInfo__block block">
            <div class="addressInfo__block_text">
              Адрес клиента
            </div>
            <EntryField v-for="addressInfo of addressInfo"
                        v-bind:key="addressInfo.name"
                        v-bind:type='addressInfo.type'
                        v-bind:name="addressInfo.name"
                        v-bind:class="addressInfo.class"
                        v-bind:options="addressInfo.options"
                        v-bind:required="addressInfo.required"
                        v-bind:title="addressInfo.label"/>
          </div>
        </form>
      </div>

    </div>
  </div>

</template>

<script>
import EntryField from "@/components/EntryField/EntryField";

export default {
  props: ['addressInfo'],
  components: {
    EntryField
  }
}
</script>

<style scoped>

</style>