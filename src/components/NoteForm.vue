<script setup lang="ts">
import { ref } from 'vue'
import type { DateValue } from '@internationalized/date'
import { DateFormatter, getLocalTimeZone } from '@internationalized/date'
import { Card, CardContent } from './ui/card'
import { Textarea } from './ui/textarea'
import { Button } from './ui/button'
import { Calendar } from './ui/calendar'
import { Popover, PopoverContent, PopoverTrigger } from './ui/popover'
import { TimePicker } from './ui/time-picker'
import { FileText, Paperclip, Calendar as CalendarIcon } from 'lucide-vue-next'
import { cn } from '@/lib/utils'

const df = new DateFormatter('pt-BR', {
  dateStyle: 'short',
})

const activeTab = ref('nota')
const date = ref<DateValue>()
const time = ref('')
const note = ref('')
</script>

<template>
  <Card>
    <CardContent class="pt-6">
      <div class="space-y-4">
        <!-- Tabs -->
        <div class="flex border-b">
          <button
            @click="activeTab = 'nota'"
            class="flex items-center gap-2 px-4 pb-3 text-sm font-medium transition-colors relative"
            :class="[
              activeTab === 'nota'
                ? 'text-gray-900'
                : 'text-gray-500 hover:text-gray-700'
            ]"
          >
            <FileText class="h-4 w-4" />
            Nota
            <div
              v-if="activeTab === 'nota'"
              class="absolute bottom-0 left-0 right-0 h-0.5 bg-cyan-400"
            />
          </button>
          <button
            @click="activeTab = 'anexo'"
            class="flex items-center gap-2 px-4 pb-3 text-sm font-medium transition-colors relative"
            :class="[
              activeTab === 'anexo'
                ? 'text-gray-900'
                : 'text-gray-500 hover:text-gray-700'
            ]"
          >
            <Paperclip class="h-4 w-4" />
            Anexar arquivo
            <div
              v-if="activeTab === 'anexo'"
              class="absolute bottom-0 left-0 right-0 h-0.5 bg-cyan-400"
            />
          </button>
        </div>
        
        <!-- Nota Tab Content -->
        <div v-if="activeTab === 'nota'" class="space-y-4">
          <div class="grid grid-cols-2 gap-4">
            <div class="space-y-2">
              <label class="text-sm font-medium text-gray-700">Data</label>
              <Popover>
                <PopoverTrigger as-child>
                  <Button
                    variant="outline"
                    :class="cn(
                      'w-full justify-start text-left font-normal',
                      !date && 'text-muted-foreground',
                    )"
                  >
                    <CalendarIcon class="mr-2 h-4 w-4" />
                    {{ date ? df.format(date.toDate(getLocalTimeZone())) : "Selecione uma data" }}
                  </Button>
                </PopoverTrigger>
                <PopoverContent class="w-auto p-0">
                  <Calendar v-model="date" initial-focus />
                </PopoverContent>
              </Popover>
            </div>
            
            <div class="space-y-2">
              <label class="text-sm font-medium text-gray-700">Horário</label>
              <TimePicker v-model="time" placeholder="09:00" />
            </div>
          </div>
          
          <div class="space-y-2">
            <label class="text-sm font-medium text-gray-700">Nota</label>
            <Textarea 
              v-model="note"
              placeholder="Registre aqui acontecimentos importantes que ocorreram durante a negociação."
              class="min-h-[120px] resize-none"
            />
          </div>
          
          <div class="flex justify-end gap-2">
            <Button variant="outline" size="default">Cancelar</Button>
            <Button class="bg-cyan-400 hover:bg-cyan-500 text-white" size="default">Salvar</Button>
          </div>
        </div>
        
        <!-- Anexar arquivo Tab Content -->
        <div v-if="activeTab === 'anexo'">
          <div class="border-2 border-dashed rounded-lg p-12 text-center border-gray-300">
            <Paperclip class="h-12 w-12 mx-auto text-gray-400 mb-4" />
            <p class="text-gray-600 text-sm">Arraste arquivos aqui ou clique para selecionar</p>
          </div>
        </div>
      </div>
    </CardContent>
  </Card>
</template>
