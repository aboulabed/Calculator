<script setup>
import btn from "@/components/btn.vue";
import { invalidateTypeCache } from "vue/compiler-sfc";
const addValue = (val) => {
  let inp = document.querySelector("input.result");
  if (val == "DEL") {
    inp.value = inp.value.slice(0, -1);
  } else if (val == "AC") {
    inp.value = "";
  } else if (
    inp.value.slice(-1) == "+" ||
    inp.value.slice(-1) == "*" ||
    inp.value.slice(-1) == "/" ||
    inp.value.slice(-1) == "-"
  ) {
    if (val == "+" || val == "*" || val == "/" || val == "-") {
      inp.value = inp.value;
    } else {
      inp.value = inp.value + val;
    }
  } else if (val == "=") {
    inp.value = eval(inp.value);
  } else {
    inp.value = inp.value + val;
  }
};
</script>

<template>
  <div class="main">
    <input disabled class="result" type="text" />
    <div class="row">
      <btn v-for="(value, i) in firRow" @click="addValue(value)" :key="i"
        >{{ value }}
      </btn>
    </div>
    <div class="row">
      <btn v-for="(value, i) in socRow" @click="addValue(value)" :key="i"
        >{{ value }}
      </btn>
    </div>
    <div class="row">
      <btn v-for="(value, i) in thirdRow" @click="addValue(value)" :key="i"
        >{{ value }}
      </btn>
    </div>
    <div class="row">
      <btn v-for="(value, i) in fourthRow" @click="addValue(value)" :key="i"
        >{{ value }}
      </btn>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      firRow: ["7", "8", "9", "DEL", "AC"],
      socRow: ["4", "5", "6", "*", "/"],
      thirdRow: ["1", "2", "3", "+", "-"],
      fourthRow: ["0", ".", "="],
    };
  },
};
</script>
<style lang="scss" scoped>
.main {
  margin: 20px auto;
  text-align: center;
  width: 60%;
  height: 100%;
  input.result {
    width: 100%;
    background-color: #1a1a1a;
    border: none;
    padding: 3px 10px;
    border-radius: 6px;
    margin-bottom: 15px;
    height: 35px;
    color: #fff;
  }
  .row {
    height: 60px;
    &:last-of-type .btn {
      width: calc(100% / 3);
    }
    display: flex;
  }
}
</style>
