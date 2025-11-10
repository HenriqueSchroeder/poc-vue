<script setup lang="ts">
import { ref } from 'vue'
import { Input } from './ui/input'
import { ChevronRight } from 'lucide-vue-next'

const props = defineProps<{
  label: string
  placeholder?: string
  expanded?: boolean
}>()

const isExpanded = ref(props.expanded ?? false)
</script>

<template>
  <div class="border-b last:border-0">
    <button
      @click="isExpanded = !isExpanded"
      class="flex w-full items-center justify-between py-3 text-sm font-medium text-gray-700 hover:text-gray-900 transition-colors"
    >
      <span>{{ label }}</span>
      <ChevronRight 
        class="h-4 w-4 transition-transform"
        :class="{ 'rotate-90': isExpanded }"
      />
    </button>
    
    <div
      v-if="isExpanded"
      class="pb-3 space-y-2"
    >
      <Input 
        :placeholder="placeholder || 'Exemplo de campo'"
        class="text-sm"
      />
      <Input 
        :placeholder="placeholder ? `${placeholder} 2` : 'Exemplo de campo 2'"
        class="text-sm"
      />
      <button class="text-sm text-gray-500 hover:text-gray-700">
        Exibir todos os campos etapa
      </button>
    </div>
  </div>
</template>
