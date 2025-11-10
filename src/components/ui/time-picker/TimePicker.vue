<script setup lang="ts">
import { ref, computed } from 'vue'
import { Button } from '../button'
import { Popover, PopoverContent, PopoverTrigger } from '../popover'
import { Clock } from 'lucide-vue-next'
import { cn } from '@/lib/utils'

const props = defineProps<{
  modelValue?: string
  placeholder?: string
}>()

const emit = defineEmits<{
  (e: 'update:modelValue', value: string): void
}>()

const hours = ref('09')
const minutes = ref('00')

const displayValue = computed(() => {
  if (props.modelValue) {
    return props.modelValue
  }
  return ''
})

const updateTime = () => {
  const timeValue = `${hours.value}:${minutes.value}`
  emit('update:modelValue', timeValue)
}

const setHours = (value: string) => {
  const num = parseInt(value) || 0
  hours.value = Math.min(23, Math.max(0, num)).toString().padStart(2, '0')
  updateTime()
}

const setMinutes = (value: string) => {
  const num = parseInt(value) || 0
  minutes.value = Math.min(59, Math.max(0, num)).toString().padStart(2, '0')
  updateTime()
}

const hourOptions = Array.from({ length: 24 }, (_, i) => i.toString().padStart(2, '0'))
const minuteOptions = Array.from({ length: 60 }, (_, i) => i.toString().padStart(2, '0'))
</script>

<template>
  <Popover>
    <PopoverTrigger as-child>
      <Button
        variant="outline"
        :class="cn(
          'w-full justify-start text-left font-normal',
          !displayValue && 'text-muted-foreground',
        )"
      >
        <Clock class="mr-2 h-4 w-4" />
        {{ displayValue || placeholder || "Selecione o horário" }}
      </Button>
    </PopoverTrigger>
    <PopoverContent class="w-auto p-4">
      <div class="flex items-center gap-2">
        <div class="flex flex-col items-center">
          <label class="text-xs text-gray-500 mb-2">Hora</label>
          <div class="flex flex-col gap-1 max-h-[200px] overflow-y-auto border rounded p-1">
            <button
              v-for="hour in hourOptions"
              :key="hour"
              @click="setHours(hour)"
              class="px-3 py-1 text-sm rounded hover:bg-accent transition-colors"
              :class="hours === hour ? 'bg-cyan-400 text-white hover:bg-cyan-500' : ''"
            >
              {{ hour }}
            </button>
          </div>
        </div>
        
        <span class="text-2xl font-semibold mt-6">:</span>
        
        <div class="flex flex-col items-center">
          <label class="text-xs text-gray-500 mb-2">Minuto</label>
          <div class="flex flex-col gap-1 max-h-[200px] overflow-y-auto border rounded p-1">
            <button
              v-for="minute in minuteOptions"
              :key="minute"
              @click="setMinutes(minute)"
              class="px-3 py-1 text-sm rounded hover:bg-accent transition-colors"
              :class="minutes === minute ? 'bg-cyan-400 text-white hover:bg-cyan-500' : ''"
            >
              {{ minute }}
            </button>
          </div>
        </div>
      </div>
    </PopoverContent>
  </Popover>
</template>
