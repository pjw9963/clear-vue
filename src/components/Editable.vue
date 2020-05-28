<template>
  <div
    ref="editable"
    contenteditable
    v-on="listeners"
  ></div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: '',
    },
  },
  computed: {
    listeners() {
      return { ...this.$listeners, input: this.onInput };
    },
  },
  mounted() {
    this.$refs.editable.innerText = this.value;
  },
  methods: {
    onInput(e) {
      this.$emit('input', e.target.innerText);
    },
  },
};
</script>

<style scoped>
    div {
        width: 100%;        
        word-break: break-all;
        text-align: start;
        outline: none;
    }
</style>