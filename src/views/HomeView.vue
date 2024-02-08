<script setup>
import btn from "@/components/btn.vue";
const addValue = (val) => {
  let inp = document.querySelector("input.result");
  if (!isNaN(val) && val != "0") {
    inp.value = inp.value + val;
  } else if (val == "=") {
    if (
      inp.value.length == 0 ||
      inp.value.slice(-1) == "+" ||
      inp.value.slice(-1) == "-" ||
      inp.value.slice(-1) == "/" ||
      inp.value.slice(-1) == "*"
    ) {
      ;
    } else {
      inp.value = eval(inp.value);
    }
  } else if (val == "DEL") {
    inp.value = inp.value.slice(0, -1);
  } else if (val == "AC") {
    inp.value = "";
  } else if (val == ".") {
    if (inp.value.slice(-1) == "." || inp.value.length == 0) {
      ;
    } else {
      inp.value = inp.value + val;
    }
  }else if(val == "0"){
    if (inp.value.length > 0 && 
      inp.value.slice(-1) !== "+" &&
      inp.value.slice(-1) !== "-" &&
      inp.value.slice(-1) !== "/" &&
      inp.value.slice(-1) !== "*"){
      inp.value = inp.value + val;

      
    }
  } else {
    if (
      inp.value.length == 0 ||
      inp.value.slice(-1) == "+" ||
      inp.value.slice(-1) == "-" ||
      inp.value.slice(-1) == "/" ||
      inp.value.slice(-1) == "*"
    ) {
      ;
    } else {
      inp.value = inp.value + val;
    }
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
  margin: 20px;
  text-align: center;
  width: 97vw;
  height: calc(65vh - 10px);
  input.result {
    width: calc(100% - 10px);
    background-color: #1a1a1a;
    border: none;
    padding: 25px;
    border-radius: 8px;
    margin-bottom: 15px;
    height: 85px;
    font-size: 40px;
    color: #fff;
    cursor: text;
  }
  .row {
    height: calc(100% / 3);
    .btn {
      font-size: 40px;
      border-radius: 8px;
      cursor: pointer;
    }
    &:last-of-type .btn {
      width: calc(100% / 3);
    }
    display: flex;
  }
}
</style>
