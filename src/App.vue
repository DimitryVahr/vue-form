<template>
  <div id="app">
    <app-form>
      <app-input placeholder="Placeholder" error="Заполните поле" />
      <app-textarea placeholder="Placeholder" error="Заполните поле" />
    </app-form>
  </div>
</template>

<script>
import AppForm from "./components/AppForm.vue";
import AppInput from "./components/AppInput.vue";
import AppTextarea from "./components/AppTextarea.vue";
export default {
  components: {
    AppForm,
    AppInput,
    AppTextarea,
  },
};
</script>