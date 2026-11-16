<script setup>
defineProps({
  quotes: Array
})
</script>

<template>
  <div>
    <h3>Список усіх цитат:</h3>
    <ul>
  
      <li v-for="(q, index) in quotes" :key="index">
        {{ q.text }} - <b>{{ q.author }}</b>
      </li>
    </ul>
  </div>
</template>