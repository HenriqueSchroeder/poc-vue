<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from './ui/card'
import HistoryStatusItem from './HistoryStatusItem.vue'
import HistoryNoteItem from './HistoryNoteItem.vue'
import HistorySaleItem from './HistorySaleItem.vue'
import HistoryBudgetItem from './HistoryBudgetItem.vue'
import HistoryCatalogItem from './HistoryCatalogItem.vue'
import HistoryCatalogSendItem from './HistoryCatalogSendItem.vue'
import HistoryContactItem from './HistoryContactItem.vue'

export interface HistoryItemBase {
  id: string
  date: string
  time: string
  stage: string
  assignee?: string
}

export interface HistoryStatusEvent extends HistoryItemBase {
  type: 'status'
  title: string
  description?: string
  user: string
}

export interface HistoryNoteEvent extends HistoryItemBase {
  type: 'note'
  assignee: string
}

export interface HistorySaleEvent extends HistoryItemBase {
  type: 'sale'
  title: string
  amount: string
  assignee: string
}

export interface HistoryBudgetEvent extends HistoryItemBase {
  type: 'budget'
  title: string
  amount: string
  assignee: string
}

export interface HistoryCatalogEvent extends HistoryItemBase {
  type: 'catalog'
  title: string
  assignee: string
}

export interface HistoryCatalogSendEvent extends HistoryItemBase {
  type: 'catalog-send'
  title: string
  assignee: string
  status?: string
}

export interface HistoryContactEvent extends HistoryItemBase {
  type: 'contact'
  title: string
  assignee: string
}

export type HistoryEvent = 
  | HistoryStatusEvent 
  | HistoryNoteEvent 
  | HistorySaleEvent 
  | HistoryBudgetEvent
  | HistoryCatalogEvent
  | HistoryCatalogSendEvent
  | HistoryContactEvent

export interface HistoryGroup {
  date: string
  events: HistoryEvent[]
}

defineProps<{
  groups: HistoryGroup[]
}>()
</script>

<template>
  <Card>
    <CardHeader>
      <CardTitle class="text-base font-semibold">Histórico</CardTitle>
    </CardHeader>
    <CardContent class="space-y-6">
      <div v-for="group in groups" :key="group.date" class="space-y-4">
        <div class="text-sm text-gray-500 font-medium">{{ group.date }}</div>
        
        <div class="space-y-3">
          <template v-for="event in group.events" :key="event.id">
            <HistoryStatusItem
              v-if="event.type === 'status'"
              :title="event.title"
              :description="event.description"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :user="event.user"
            />
            
            <HistoryNoteItem
              v-else-if="event.type === 'note'"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :assignee="event.assignee"
            />
            
            <HistorySaleItem
              v-else-if="event.type === 'sale'"
              :title="event.title"
              :amount="event.amount"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :assignee="event.assignee"
            />
            
            <HistoryBudgetItem
              v-else-if="event.type === 'budget'"
              :title="event.title"
              :amount="event.amount"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :assignee="event.assignee"
            />
            
            <HistoryCatalogItem
              v-else-if="event.type === 'catalog'"
              :title="event.title"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :assignee="event.assignee"
            />
            
            <HistoryCatalogSendItem
              v-else-if="event.type === 'catalog-send'"
              :title="event.title"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :assignee="event.assignee"
              :status="event.status"
            />
            
            <HistoryContactItem
              v-else-if="event.type === 'contact'"
              :title="event.title"
              :date="event.date"
              :time="event.time"
              :stage="event.stage"
              :assignee="event.assignee"
            />
          </template>
        </div>
      </div>
    </CardContent>
  </Card>
</template>
