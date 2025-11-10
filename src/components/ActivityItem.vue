<script setup lang="ts">
import { Card } from './ui/card'
import { Avatar, AvatarFallback } from './ui/avatar'
import { Badge } from './ui/badge'
import { Calendar, Clock, FileText } from 'lucide-vue-next'

defineProps<{
  title: string
  date: string
  time: string
  stage: string
  assignee: string
  completed?: boolean
}>()
</script>

<template>
  <Card class="p-4 hover:shadow-md transition-shadow cursor-pointer">
    <div class="flex items-start justify-between">
      <div class="flex items-start gap-3 flex-1">
        <FileText class="h-5 w-5 text-gray-400 mt-0.5" />
        <div class="flex-1 min-w-0">
          <h4 class="font-medium text-gray-900 mb-2">{{ title }}</h4>
          <div class="flex items-center gap-4 text-sm text-gray-500">
            <div class="flex items-center gap-1">
              <Calendar class="h-3.5 w-3.5" />
              <span>{{ date }}</span>
            </div>
            <div class="flex items-center gap-1">
              <Clock class="h-3.5 w-3.5" />
              <span>{{ time }}</span>
            </div>
            <Badge variant="secondary" class="text-xs">
              {{ stage }}
            </Badge>
          </div>
        </div>
      </div>
      
      <div class="flex items-center gap-3">
        <input 
          type="checkbox" 
          :checked="completed"
          class="h-4 w-4 rounded border-gray-300 text-cyan-400 focus:ring-cyan-400"
        />
        <Avatar class="h-6 w-6">
          <AvatarFallback class="bg-purple-500 text-white text-xs">
            {{ assignee.split(' ').map(n => n[0]).join('').substring(0, 2) }}
          </AvatarFallback>
        </Avatar>
      </div>
    </div>
  </Card>
</template>
