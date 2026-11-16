<script setup>
import { computed, ref } from 'vue'
import QuoteDisplay from './components/QuoteDisplay.vue'
import QuotesList from './components/QuotesList.vue'



const quotes = ref([
  { text: 'Ніколи не відкладай на завтра те, що можна зробити післязавтра так само добре.', author: 'Марк Твен' },
  { text: 'Мені нема чого заявити, окрім своєї геніальності.', author: 'Оскар Уальд' },
  { text: 'Єдине, що я знаю, це те, що я нічого не знаю.', author: 'Сократ' },
  
])

const currentQuote = ref(null)

const wordCount = computed(() => {
  if (!currentQuote.value) return 0 
  return currentQuote.value.text.trim().split(/\s+/).length
})

function newQuote() {
  const randomIndex = Math.floor(Math.random() * quotes.value.length)
  currentQuote.value = quotes.value[randomIndex]
  
}
const newText = ref('')
const newAuthor = ref('')

function addQuote() {
  if (!newText.value.trim() || !newAuthor.value.trim()) return

  quotes.value.push({
    text: newText.value.trim(),
    author: newAuthor.value.trim()
  })

  newText.value = ''
  newAuthor.value = ''
}

</script>

<template>
  <button @click="newQuote">Нова цитата</button>

  <div v-if="currentQuote">
    <QuoteDisplay :quote="currentQuote" />
    <form @submit.prevent="addQuote">
      <p v-if="wordCount > 0">Кількість слів: {{ wordCount }}</p>
  <h3>Додати цитату</h3>
  <input v-model="newText" placeholder="Текст цитати" />
  <input v-model="newAuthor" placeholder="Автор" />
  <button type="submit">Додати</button>
</form>

  </div>
  <p v-else>Натисніть кнопку, щоб отримати цитату.</p>

  <QuotesList :quotes="quotes" />

</template>

