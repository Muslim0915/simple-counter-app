<script lang="ts" setup>
import { computed, ref } from 'vue'
import AppCounter from "@/components/AppCounter.vue";


interface CounterConfig {
  startValue: number
  step: number
}

const counters: CounterConfig[] = [
  { startValue: 0, step: 1 },
  { startValue: 10, step: 2 },
  { startValue: 5, step: 3 },
]

const values = ref<number[]>(counters.map(counter => counter.startValue))

const updateCount = (index: number, value: number) => {
  values.value[index] = value
}

const total = computed(() => {
  return values.value.reduce((acc, val) => acc + val, 0)
})
</script>
<template>
  <div class="container">
    <div class="counter-list">
      <AppCounter
          v-for="(cfg, index) in counters"
          :key="index"
          :startValue="cfg.startValue"
          :step="cfg.step"
          @update="updateCount(index, $event)"
      />
      <div class="total">
        Total: <span>{{ total }}</span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.container{
  display: flex;
  justify-content: center;
  align-items: center;
  flex: 1 1 0;
}
.counter-list {
  border: 1px solid $primary;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 1rem;

  .total {
    margin-top: 2rem;
    font-weight: bold;
    font-size: 1.5rem;
    span {
      color: #007acc;
      font-size: 20px;
    }
  }
}
</style>
