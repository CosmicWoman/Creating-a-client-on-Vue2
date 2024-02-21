<template>
  <div>

    <div class="typeInput" v-if='type === "input"'>
      <div class="typeInput -title" v-if="!required">{{title}}</div>
      <div class="typeInput -title" v-if="required">{{title}}*</div>

      <input type="text"
             :id={name}
             class="inputStyle"
      />

      <div class="error" v-if="v.name.$errors">Ошибка</div>

    </div>

    <div class="typeInputNum" v-if='type === "inputNum"'>
      <div class="typeInputNum -title" v-if="!required">{{ title }}</div>
      <div class="typeInputNum -title" v-if="required">{{ title }}*</div>
      <input type="text"
             :id='{name}'
             class="inputStyle"
      />
    </div>

    <div class="typeInputDate" v-if='type === "inputDate"'>
      <div class="typeInputDate -title" v-if="!required">{{ title }}</div>
      <div class="typeInputDate -title" v-if="required">{{ title }}*</div>
      <input type="date"
             :id={name}
             class="inputStyle"
      />
    </div>

    <div class="typeSelector" v-if='type === "selector"'>
      <div class="typeInputNum -title" v-if="!required">{{ title }}</div>
      <div class="typeInputNum -title" v-if="required">{{ title }}*</div>
      <select :id={name}
              class="inputStyle">
        <option v-for="option in options"
                :key="option"
                :value="option">
          {{ option }}
        </option>
      </select>
    </div>

    <div class="typeCheckbox" v-if='type === "checkbox"'>
      <div class="typeCheckbox -title" v-if="!required">{{ title }}</div>
      <div class="typeCheckbox -title" v-if="required">{{ title }}*</div>
      <input type="checkbox"
             :id={name}
             class="checkedStyle"
      />
    </div>

    <div class="typeRadio" v-if='type === "radio"'>
      <div class="typeRadio -title">{{ title }}</div>
      <div class="typeRadio -title" v-if="required">{{ title }}*</div>
      <div class="typeRadio radioBlock">
        <div class="radioBlock male">
          <input type="radio"
                 id='male'
                 :class={className}
                 value="male"
                 v-model="radioCheck"
          />
          <label for="male" class="radio -title">
            М
          </label>
        </div>

        <div class="radioBlock female">
          <input type="radio"
                 id="female"
                 :class={className}
                 value="female"
                 v-model="radioCheck"
          />
          <label for="female" class="radio -title">
            Ж
          </label>
        </div>

      </div>
    </div>

    <div class="typeMultiSel" v-if='type === "multSelector"'>
      <div class="typeMultiSel -title" v-if="!required">{{ title }}</div>
      <div class="typeMultiSel -title" v-if="required">{{ title }}*</div>
      <select :id={name}
              class="multiSelStyle"
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
  // props:
  //     {
  //   title: String,
  //   type: String,
  //   name: String,
  //   className: String,
  //   options: [String],
  //   required: Boolean,
  //   v: String
  // },

  props: ['formData', 'formName', 'v'],

  data() {
    return {
      radioCheck: '',
      arrChecked: [],
    }
  },

}
</script>

<style scoped lang="sass" src="../../../style/inputStyle.sass">

</style>