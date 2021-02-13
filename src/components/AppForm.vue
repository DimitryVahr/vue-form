  
<template>
  <form>
    <slot></slot>
  </form>
</template>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  width: 300px;
  --placeholder: #a7a7b3;
  --placeholder-active: #2d7cdf;
  --input-text: #192630;
  --border: #e3e3ea;
  --border-acrive: #192630;
  --caret: #2d7cdf;
  --background-input: #ffffff;
  --shadow: #99c0f0;
  --disabled: #f5f5f7;
  --error: #d51a1a;
  --error-shadow: #EEA3A3;
}
form > *:not(:first-child) {
  margin-top: 30px;
}
</style>