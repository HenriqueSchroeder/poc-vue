<script setup lang="ts">
import { computed } from 'vue'
import { Check, MapPin } from 'lucide-vue-next'

const props = defineProps<{
  currentStage: string
}>()

const emit = defineEmits<{
  (e: 'update:currentStage', value: string): void
}>()

const stages = [
  { id: 'qualificacao', label: 'Qualificação' },
  { id: 'contato', label: 'Contato' },
  { id: 'proposta', label: 'Proposta' },
  { id: 'follow', label: 'Follow' },
  { id: 'fechamento', label: 'Fechamento' }
]

const currentIndex = computed(() => 
  stages.findIndex(s => s.id === props.currentStage)
)

const handleStageClick = (stageId: string) => {
  emit('update:currentStage', stageId)
}
</script>

<template>
  <div class="border-b bg-white px-6 py-3">
    <div class="flex items-center gap-3">
      <button
        v-for="(stage, index) in stages" 
        :key="stage.id"
        @click="handleStageClick(stage.id)"
        class="flex-1 flex items-center justify-center gap-2 px-4 py-2 rounded border text-sm font-medium transition-all"
        :class="[
          index === currentIndex
            ? 'bg-cyan-50 border-cyan-400 text-cyan-700'
            : index < currentIndex
            ? 'bg-cyan-50 border-cyan-400 text-cyan-700'
            : 'bg-white border-gray-300 text-gray-700 hover:bg-gray-50'
        ]"
      >
        <Check 
          v-if="index < currentIndex" 
          class="h-4 w-4" 
        />
        <MapPin 
          v-else-if="index === currentIndex" 
          class="h-4 w-4" 
        />
        <span>{{ stage.label }}</span>
      </button>
    </div>
  </div>
</template>
