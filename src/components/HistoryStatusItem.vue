<script setup lang="ts">
import { TrendingUp, Clock } from 'lucide-vue-next'
import { Avatar, AvatarFallback } from './ui/avatar'
import { Badge } from './ui/badge'

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
  <div class="bg-white rounded-lg border p-4 hover:shadow-md transition-shadow cursor-pointer">
    <div class="flex items-start gap-3">
      <TrendingUp class="h-5 w-5 text-cyan-400 mt-0.5 shrink-0" />
      <div class="flex-1 min-w-0">
        <h4 class="font-medium text-gray-900 mb-1">{{ title }}</h4>
        <p v-if="description" class="text-sm text-gray-600 mb-3">
          <span class="font-medium">Devolutivo representante:</span> {{ description }}
        </p>
        
        <div class="flex items-center gap-4 text-sm text-gray-500">
          <div class="flex items-center gap-1">
            <Clock class="h-3.5 w-3.5" />
            <span>{{ date }}</span>
            <span>{{ time }}</span>
          </div>
          <Badge variant="secondary" class="text-xs">
            {{ stage }}
          </Badge>
          <div class="flex items-center gap-2 ml-auto">
            <Avatar class="h-5 w-5">
              <AvatarFallback class="bg-purple-500 text-white text-[10px]">
                {{ user.substring(0, 2) }}
              </AvatarFallback>
            </Avatar>
            <span class="text-xs text-purple-600">{{ user }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
