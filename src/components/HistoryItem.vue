<script setup lang="ts">
import { Card } from './ui/card'
import { Avatar, AvatarFallback } from './ui/avatar'
import { Badge } from './ui/badge'
import { Calendar, Clock, TrendingUp } from 'lucide-vue-next'

defineProps<{
  title: string
  description?: string
  date: string
  time: string
  stage: string
  user: string
}>()
</script>

<template>
  <Card class="p-4">
    <div class="flex items-start gap-3">
      <TrendingUp class="h-5 w-5 text-cyan-400 mt-0.5" />
      <div class="flex-1">
        <h4 class="font-medium text-gray-900 mb-1">{{ title }}</h4>
        <p v-if="description" class="text-sm text-gray-600 mb-3">{{ description }}</p>
        
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
          <div class="flex items-center gap-2 ml-auto">
            <Avatar class="h-6 w-6">
              <AvatarFallback class="bg-purple-500 text-white text-xs">
                {{ user.substring(0, 2) }}
              </AvatarFallback>
            </Avatar>
            <span class="text-xs">{{ user }}</span>
          </div>
        </div>
      </div>
    </div>
  </Card>
</template>
