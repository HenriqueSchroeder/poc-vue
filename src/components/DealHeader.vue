<script setup lang="ts">
import { Button } from './ui/button'
import { Avatar, AvatarFallback } from './ui/avatar'
import { ChevronLeft, Plus, X } from 'lucide-vue-next'

defineProps<{
    dealNumber: string
    consultantName: string
    deadline?: string
    closingConsultant?: string
}>()
</script>

<template>
    <header class="border-b bg-white px-6 py-3">
        <div class="flex items-center justify-between">
            <div class="flex items-center gap-3">
                <Button variant="ghost" size="icon-sm">
                    <ChevronLeft class="h-5 w-5" />
                </Button>
                <div class="text-xs text-gray-500">
                    Funil de vendas / <span class="font-medium text-gray-900">Negociação</span>
                </div>
            </div>

            <div class="flex items-center gap-8">
                <div>
                    <div class="text-xs text-gray-500 mb-0.5">Código da negociação</div>
                    <div class="border border-dashed border-gray-300 rounded text-sm font-semibold text-gray-900 p-1 h-9 flex items-center min-w-[140px]">
                        {{ dealNumber }}
                    </div>
                </div>

                <div>
                    <div class="text-xs text-gray-500 mb-0.5">Consultor de vendas interno</div>
                    <div class="border border-dashed border-gray-300 rounded flex items-center gap-2 p-1 h-9 min-w-[140px]">
                        <Avatar class="h-7 w-7">
                            <AvatarFallback class="bg-blue-600 text-white text-xs font-medium">
                                SE
                            </AvatarFallback>
                        </Avatar>
                        <span class="text-sm font-medium text-gray-900">{{ consultantName }}</span>
                    </div>
                </div>

                <div>
                    <div class="text-xs text-gray-500 mb-1">Resultado da negociação</div>
                    <div class="flex gap-2">
                        <Button size="sm" class="bg-cyan-400 hover:bg-cyan-500 text-white h-8 px-3 gap-1.5">
                            <Plus class="h-4 w-4" />
                            Ganha
                        </Button>
                        <Button size="sm" class="bg-red-500 hover:bg-red-600 text-white h-8 px-3 gap-1.5">
                            <X class="h-4 w-4" />
                            Perdida
                        </Button>
                    </div>
                </div>
            </div>
        </div>
    </header>
</template>
