<template>
  <div>

    <div class="typeInput" v-if='type === "input"'>
      <div class="typeInput__title" v-if="!required">{{ title }}</div>
      <div class="typeInput__title" v-if="required">{{ title }}*</div>
      <input type="text"
             :id={name}
             :class={className}
      />
    </div>

    <div class="typeInputNum" v-if='type === "inputNum"'>
      <div class="typeInputNum__title" v-if="!required">{{ title }}</div>
      <div class="typeInputNum__title" v-if="required">{{ title }}*</div>
      <input type="text"
             :id='{name}'
             :class="{className}"
      />
    </div>

    <div class="typeInputDate" v-if='type === "inputDate"'>
      <div class="typeInputDate__title" v-if="!required">{{ title }}</div>
      <div class="typeInputDate__title" v-if="required">{{ title }}*</div>
      <input type="date"
             :id={name}
             :class={className}
      />
    </div>

    <div class="typeSelector" v-if='type === "selector"'>
      <div class="typeInputNum__title" v-if="!required">{{ title }}</div>
      <div class="typeInputNum__title" v-if="required">{{ title }}*</div>
      <select :id={name}
              :class={className}>
        <option v-for="option in options"
                :key="option"
                :value="option">
          {{ option }}
        </option>
      </select>
    </div>

    <div class="typeCheckbox" v-if='type === "checkbox"'>
      <div class="typeCheckbox__title" v-if="!required">{{ title }}</div>
      <div class="typeCheckbox__title" v-if="required">{{ title }}*</div>
      <input type="checkbox"
             :id={name}
             :class={className}
      />
    </div>

    <div class="typeCheckbox" v-if='type === "radio"'>
      <div class="typeCheckbox__title">{{ title }}</div>
      <div class="typeCheckbox__title" v-if="required">{{ title }}*</div>
      <div class="radio__title">
        М
      </div>
      <input type="radio"
             :id={name}
             :class={className}
             value="male"
      />

      <div class="radio__title">
        Ж
      </div>
      <input type="radio"
             :id={name}
             :class={className}
             value="female"
      />
    </div>

    <div class="typeMultiSel" v-if='type === "multSelector"'>
      <div class="typeMultiSel__title" v-if="!required">{{ title }}</div>
      <div class="typeMultiSel__title" v-if="required">{{ title }}*</div>
      <select :id={name}
              :class={className}
              :size="options.length"
              multiple>
        <option v-for="option in options"
                :key="option"
                :value="option">
          {{ option }}
        </option>
      </select>
    </div>
  </div>


</template>

<script>
export default {
  props: {
    title: String,
    type: String,
    name: String,
    className: String,
    options: [String],
    required: Boolean
  }
}
</script>

<style scoped>

</style>