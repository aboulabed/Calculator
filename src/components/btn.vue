<script setup>
const props = defineProps({
  content: {
    type: String,
    required: false,
  },
});
</script>
<template>
  <div class="btn"><slot></slot></div>
</template>

<style lang="scss" scoped>
.btn {
  background: #1a1a1a;
  color: #fff;
  margin: 7px;
  padding: 5px 10px;
  border-radius: 5px;
  width: 20%;    align-items: center;
    display: flex;
    justify-content: center;
}
</style>
