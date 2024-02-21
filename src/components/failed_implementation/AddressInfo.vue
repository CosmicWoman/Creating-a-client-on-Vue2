<template>

  <div class="addressInfo">
    <div class="addressInfo -container container">

      <div class="addressInfo -content">

        <form id="form" @submit.prevent="onSubmit">
          <div class="addressInfo -block block">
            <div class="addressInfo -block_text">
              Адрес клиента
            </div>
            <EntryField v-for="addressInfo of addressInfo"
                        v-bind:key="addressInfo.name"
                        v-bind:type='addressInfo.type'
                        v-bind:name="addressInfo.name"
                        v-bind:class="addressInfo.class"
                        v-bind:options="addressInfo.options"
                        v-bind:required="addressInfo.required"
                        v-bind:title="addressInfo.title"/>
          </div>
        </form>
      </div>

    </div>
  </div>

</template>

<script>
import EntryField from "@/components/failed_implementation/EntryField/EntryField";

export default {
  props: ['addressInfo'],
  components: {
    EntryField
  }
}
</script>

<style scoped lang="sass" src="../../style/styleBlockInfo.sass">

</style>