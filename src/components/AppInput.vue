<template>
  <label class="input">
    <input
      ref="input"
      class="input__fluid"
      v-model="value"
      :type="type"
      value=""
    />
    <span class="input__placeholder" @click="clear">{{ placeholder }}</span>
    <span class="input__helper-text">{{ errorMessage }}</span>
    <div class="input__icon">
      <div class="icon-cross" @click="clear"></div>
      <div class="icon-error"></div>
    </div>
  </label>
</template>

<script>
export default {
  name: "app-input",
  data() {
    return {
      value: "",
    };
  },
  props: {
    placeholder: {
      type: String,
      isRequired: true,
    },
    type: {
      type: String,
      default: "text",
    },
    errorMessage: {
      type: String,
      default: "Заполните поле",
    },
  },
  watch: {
    value() {
      this.$refs.input.setAttribute("value", this.value);
    },
  },
  methods: {
    clear() {
      this.value = "";
    },
  },
};
</script>

<style lang="scss" scoped>
.input {
  display: inline-block;
  position: relative;
  width: auto;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;

  &__placeholder {
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    color: var(--placeholder);
    position: absolute;
    left: 12px;
    top: 0;
    transform-origin: 0 0;
    transform: translate(0, 16px);
    background-color: transparent;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    pointer-events: none;
    max-width: 95%;
    overflow: hidden;
    transition: transform 0.2s ease-out, color 0.2s ease-out;
  }
  &__helper-text {
    display: none;
    position: absolute;
    font-style: normal;
    font-weight: normal;
    line-height: 24px;
    letter-spacing: 0.02em;
    font-size: 12px;
  }
  &__fluid {
    width: 100%;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    overflow: hidden;
    text-overflow: ellipsis;
    transition: border 0.2s ease-out, box-shadow 0.2s ease-out;
    background: var(--background-input);
    height: 56px;
    box-sizing: border-box;
    caret-color: var(--caret);
    padding: 26px 48px 6px 12px;
    border: 1px solid var(--border);
    border-radius: 4px;
    outline: none;
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 24px;
    display: flex;
    align-items: center;
    color: var(--input-text);
  }
  &__icon {
    position: absolute;
    width: 24px;
    height: 24px;
    top: 16px;
    right: 12px;
  }
  &__icon > * {
    width: 100%;
    height: 100%;
  }
  &__icon .icon-error {
    display: none;
    background-image: url("data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTEyIDJDNi40OCAyIDIgNi40OCAyIDEyQzIgMTcuNTIgNi40OCAyMiAxMiAyMkMxNy41MiAyMiAyMiAxNy41MiAyMiAxMkMyMiA2LjQ4IDE3LjUyIDIgMTIgMlpNMTMgMTdIMTFWMTVIMTNWMTdaTTEzIDEzSDExVjdIMTNWMTNaIiBmaWxsPSIjRDUxQTFBIi8+Cjwvc3ZnPgo=");
  }
  &__icon .icon-cross {
    cursor: pointer;
    display: none;
    background-image: url("data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHBhdGggZD0iTTEyIDJDNi40NyAyIDIgNi40NyAyIDEyQzIgMTcuNTMgNi40NyAyMiAxMiAyMkMxNy41MyAyMiAyMiAxNy41MyAyMiAxMkMyMiA2LjQ3IDE3LjUzIDIgMTIgMlpNMTcgMTUuNTlMMTUuNTkgMTdMMTIgMTMuNDFMOC40MSAxN0w3IDE1LjU5TDEwLjU5IDEyTDcgOC40MUw4LjQxIDdMMTIgMTAuNTlMMTUuNTkgN0wxNyA4LjQxTDEzLjQxIDEyTDE3IDE1LjU5WiIgZmlsbD0iI0E3QTdCMyIvPgo8L3N2Zz4K");
  }
}
.input__fluid:focus ~ .input__placeholder,
.input__fluid:not([value=""]) ~ .input__placeholder {
  font-weight: 500;
  line-height: 16px;
  color: var(--placeholder-active);
  transform: translate(0, 7px) scale(0.75);
}
.input:hover .input__fluid,
.input__fluid:focus {
  border: 1px solid var(--border-acrive);
}
.input__fluid:focus {
  -webkit-box-shadow: 0 0 0 3px var(--shadow);
  box-shadow: 0 0 0 3px var(--shadow);
}
.input__fluid:disabled {
  background: var(--disabled);
  box-shadow: none !important;
}
.input__fluid:disabled ~ .input__icon {
  display: none;
}
.input__fluid:disabled ~ .input__placeholder {
  background: rgba(0, 0, 0, 0);
}
.input__fluid:not([value=""]):focus ~ .input__icon .icon-cross {
  display: inline-block;
}
.input__icon .icon-cross:hover,
.input__icon .icon-cross:active {
  display: inline-block !important;
}
.input__fluid[value=""] ~ .input__icon .icon-cross {
  display: none !important;
}
.error .input {
  &__fluid {
    border: 1px solid var(--error) !important;
    caret-color: var(--error);
  }
  &__fluid:focus {
    -webkit-box-shadow: 0 0 0 3px var(--error-shadow);
    box-shadow: 0 0 0 3px var(--error-shadow);
  }
  &__icon .icon-cross {
    display: none !important;
  }
  &__icon .icon-error {
    display: inline-block;
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