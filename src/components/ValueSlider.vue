<template>
  <fieldset class="value-slider">
    <label :for="name">
      {{ name }}
      <br />
      {{ roundedValue || value }}
    </label>
    <input
      type="range"
      :name="name"
      :min="min"
      :max="max"
      :step="step"
      :value="value"
      @input="$emit('input', +$event.target.value)"
    />
  </fieldset>
</template>

<script>
export default {
  model: {
    prop: "value",
    event: "input"
  },
  props: {
    name: {
      type: String,
      required: true
    },
    min: {
      type: Number,
      default: 0
    },
    max: {
      type: Number,
      default: 100
    },
    step: {
      type: Number,
      default: 1
    },
    value: {
      type: Number,
      default: 50
    },
    round: [Boolean, String]
  },
  computed: {
    roundedValue() {
      if (this.round) {
        return Math.floor(this.value);
      }
      return 0;
    }
  }
};
</script>

<style lang="scss" scoped>
fieldset {
  user-select: none;
}
</style>

