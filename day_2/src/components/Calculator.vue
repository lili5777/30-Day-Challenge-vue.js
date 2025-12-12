<script setup>
import { ref,computed } from 'vue';

const current =ref('0');
const previous =ref(null);
const operation = ref(null);
const history =ref([]);

const display = computed(()=> current.value);

function numericDigitsCount(str){
    return (str.match(/\d/g) || []).legth;
}

function opSymbol(op){
    if (op==='*') return '×';
    if (op==='/') return '÷';
    return op;
}

function formatResult(num){
    if(!isFinite(num)) return 'Error';
    const str = String(num);
    if(str.length <=10) return trimTrailing(str);

    let p = Number(num).toPrecision(10);
    return trimTrailing(p);
}

function trimTrailing(s) {
  if (s.includes('.')) {
    s = s.replace(/(?:\.0+|(\.[0-9]*[1-9])0+)$/, '$1')
  }
  
  if (s.length > 10) s = s.slice(0, 10)
  return s
}

</script>

<template>
  
</template>