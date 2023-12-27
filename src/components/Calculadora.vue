<script setup>
import { computed, reactive } from 'vue'
const values = reactive({
  value1: null,
  value2: null,
  op: "+"
});

const operacao = computed(()=>{
  if(values.op === "+"){
    return values.value1 + values.value2;
  }
  if(values.op === "x"){
    return values.value1 * values.value2;
  }
  if(values.op === "/"){
    return values.value1 / values.value2;
  }
  if(values.op === "-"){
    return values.value1 - values.value2;
  }
})

</script>

<template>
  <div class="container">
    <div class="inputs">
      <div class="container__input">
        <input type="number" placeholder="Valor 1" v-model="values.value1">
      </div>
      <div class="container__select">
        <select v-model="values.op">
          <option>+</option>
          <option>-</option>
          <option>x</option>
          <option>/</option>
        </select>
      </div>
      <div class="container__input">
        <input type="number" placeholder="Valor 2" v-model="values.value2">
      </div>
    </div>
    <div class="container__display">
      <span>Resultado:</span>
      <span>{{ operacao }}</span>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container{
  border-radius: 10px;
  border: 2.5px solid lighten($color: #000, $amount: 50%);
  background-color: lighten($color: rgba(0,0,0), $amount: 50%);
  height: 200px;
  width: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  flex-wrap: wrap;
}

.inputs{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
}

.container__display{
  width: 100%;
  text-align: center;
  margin-top: 5px;
  display: flex;
  flex-direction: column;
  span{
    color: black;
    font-weight: bold;
    font-size: 24px;
  }
  span:nth-child(2){
    color: black;
    font-weight: bold;
    font-size: 22px;
    font-style: italic;
  }
}

.container__input{
  width: 100%;
  input{
    width: 100%;
    padding: 5px 10px;
    text-align: center;
    border: none;
    outline: none;
  }
  &:nth-child(1){
    overflow: hidden;
    border-radius: 10px 10px 0 0;
  }
  &:nth-child(3){
    overflow: hidden;
    border-radius: 0 0 10px 10px;
  }
}

.container__select{
  width: 100%;
  select{
    width: 100%;
    padding: 5px 0;
    margin: 0;
    text-align: center;
    outline: none;
  }
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}
</style>
