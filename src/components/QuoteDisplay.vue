<script setup>
defineProps({
  quote: Object,
})
</script>

<template>
     <p v-if="quote">{{ quote.text }} - {{ quote.author }}</p>
  <p v-else>Натисніть кнопку, щоб отримати цитату.</p>
</template>