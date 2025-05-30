<script setup lang="ts">
import { ref, watch } from 'vue'

interface Props {
  startValue: number
  step: number
}

const props = defineProps<Props>()
const emit = defineEmits<{
  (e: 'update', value: number): void
}>()

const count = ref(props.startValue)

const increment = () => {
  count.value += props.step
}

const decrement = () => {
  count.value -= props.step
}

watch(count, (newVal) => {
  emit('update', newVal)
})
</script>

<template>
  <div class="counter">
    <button @click="decrement">-</button>
    <span>{{ count }}</span>
    <button @click="increment">+</button>
  </div>
</template>

<style scoped lang="scss">
.counter {
  display: flex;
  align-items: center;
  gap: 1rem;

  button {
    padding: 0.5rem 1rem;
    background-color: #222;
    color: #fff;
    border: none;
    cursor: pointer;
    border-radius: 4px;

    &:hover {
      background-color: #444;
    }
  }

  span {
    font-weight: bold;
    font-size: 1.2rem;
    width: 40px;
    text-align: center;
  }
}
</style>
