<template>
  <label class="textarea">
    <textarea
      ref="textarea"
      class="textarea__fluid"
      @input="setValue"
      value=""
    />
    <span class="textarea__placeholder">{{ placeholder }}</span>
    <span class="textarea__helper-text">{{ error }}</span>
  </label>
</template>

<script>
export default {
  name: "app-textarea",
  props: {
    placeholder: {
      type: String,
      isRequired: true,
    },
    type: {
      type: String,
      default: "text",
    },
    error: {
      type: String,
      default: "Заполните поле",
    },
  },
  methods: {
    setValue(e) {
      let value = e.target.value;
      this.$refs.textarea.setAttribute("value", value);
      this.$emit("textarea", value);
    },
  },
};
</script>

<style lang="scss" scoped>
.textarea {
  display: inline-block;
  position: relative;
  width: 100%;
  &::after {
    content: "";
    display: block;
    width: calc(100% - 19px);
    position: absolute;
    height: 27px;
    border-radius: 4px;
    top: 1px;
    left: 1px;
    background-color: var(--background-input);
  }
  &__placeholder {
    cursor: text;
    position: absolute;
    left: 12px;
    top: 0;
    background-color: var(--background-input);
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    pointer-events: none;
    max-width: 95%;
    width: auto;
    transform-origin: 0 0;
    transform: translate(0, 16px);
    color: var(--placeholder);
    transition: transform 0.2s ease-out, color 0.2s ease-out;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    z-index: 1;
  }

  &__fluid {
    position: relative;
    vertical-align: top;
    width: 100%;
    display: inherit;
    background: var(--background-input);
    border: 1px solid var(--border);
    border-radius: 4px;
    box-sizing: border-box;
    font-style: normal;
    font-weight: 400;
    caret-color: var(--caret);
    min-height: 112px;
    max-height: 500px;
    max-width: 100%;
    min-width: 100%;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    padding: 28px 12px 4px;
    font-size: 16px;
    line-height: 24px;
    color: var(--input-text);
    outline: none;
    transition: border 0.2s ease-in-out, box-shadow 0.2s ease-in-out,
      -webkit-box-shadow 0.2s ease-in-out;
  }

  &__helper-text {
    font-style: normal;
    font-weight: normal;
    line-height: 24px;
    letter-spacing: 0.02em;
    color: var(--black);
    display: inline-block;
    display: none;
    font-size: 12px;
  }
  &__fluid_noresize {
    resize: none;
  }
}
.textarea__fluid:focus ~ .textarea__placeholder,
.textarea__fluid:not([value=""]) ~ .textarea__placeholder {
  line-height: 16px;
  transform: translate(0, 7px) scale(0.75);
  color: var(--placeholder-active);
}
.textarea:hover .textarea__fluid {
  border-color: var(--border-acrive);
}
.textarea__fluid:focus {
  box-shadow: 0 0 0 3px var(--shadow);
  border-color: var(--border-acrive);
}
.textarea__fluid:disabled {
  background: var(--disabled);
  box-shadow: none !important;
}
.error {
  margin-bottom: 0 !important;
}
.error .textarea {
  &__fluid {
    border: 1px solid var(--error) !important;
    caret-color: var(--error);
  }
  &__fluid:focus {
    -webkit-box-shadow: 0 0 0 3px var(--error-shadow);
    box-shadow: 0 0 0 3px var(--error-shadow);
  }
  &__fluid::placeholder {
    color: var(--error);
  }
  &__placeholder {
    color: var(--error) !important;
  }
  &__helper-text {
    color: var(--error);
    display: inline;
  }
}
</style>