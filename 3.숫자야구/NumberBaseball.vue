<template>
  <div>
    <h1>{{ result }}</h1>
    <form v-on:submit="onSubmitForm">
      <input ref="answer" v-model="value" maxlength="4" />
      <button type="submit">입력!</button>
    </form>
    <div>시도: {{ result }}</div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      value: "",
      result: "",
    };
  },
  methods: {
    onSubmitForm(e) {
      e.preventDefault();
    },
  },
};
</script>
<style></style>
