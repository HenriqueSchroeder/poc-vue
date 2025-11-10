<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from './ui/card'
import { Input } from './ui/input'
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from './ui/select'
import ActivityItem from './ActivityItem.vue'
import { Search } from 'lucide-vue-next'

export interface Activity {
  id: string
  title: string
  date: string
  time: string
  stage: string
  assignee: string
  completed?: boolean
}

defineProps<{
  activities: Activity[]
}>()
</script>

<template>
  <Card>
    <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-4">
      <CardTitle class="text-base font-semibold">Atividades pendentes</CardTitle>
      <div class="flex gap-2">
        <div class="relative">
          <Search class="absolute left-3 top-1/2 -translate-y-1/2 h-4 w-4 text-gray-400" />
          <Input 
            placeholder="Procurar registros"
            class="pl-9 w-64 h-9"
          />
        </div>
        <Select>
          <SelectTrigger class="w-48 h-9">
            <SelectValue placeholder="Todos os registros" />
          </SelectTrigger>
          <SelectContent>
            <SelectItem value="all">Todos os registros</SelectItem>
            <SelectItem value="pending">Pendentes</SelectItem>
            <SelectItem value="completed">Concluídos</SelectItem>
          </SelectContent>
        </Select>
      </div>
    </CardHeader>
    <CardContent class="space-y-3">
      <ActivityItem 
        v-for="activity in activities"
        :key="activity.id"
        :title="activity.title"
        :date="activity.date"
        :time="activity.time"
        :stage="activity.stage"
        :assignee="activity.assignee"
        :completed="activity.completed"
      />
    </CardContent>
  </Card>
</template>
