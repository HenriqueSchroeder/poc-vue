<script setup lang="ts">
import { Card, CardContent, CardHeader, CardTitle } from './ui/card'
import { Phone, Mail, Copy } from 'lucide-vue-next'

defineProps<{
    companyName: string
    companySubtitle: string
    contactName: string
    contactRole: string
    phone?: string
    landline?: string
    email?: string
}>()
</script>

<template>
    <Card class="border-0 shadow-none">
        <CardHeader class="pb-3">
            <CardTitle class="text-sm font-medium text-gray-500">Cliente</CardTitle>
        </CardHeader>
        <CardContent class="space-y-4">
            <div>
                <h3 class="font-semibold text-gray-900 text-sm leading-tight">{{ companyName }}</h3>
                <p class="text-xs text-gray-500 mt-1">{{ companySubtitle }}</p>
            </div>

            <div class="pt-2">
                <h4 class="font-semibold text-gray-900 text-sm">{{ contactName }}</h4>
                <p class="text-xs text-gray-500 mt-0.5">{{ contactRole }}</p>
            </div>

            <div class="space-y-2 pt-1">
                <div v-if="phone" class="flex items-center justify-between text-xs group">
                    <div class="flex items-center gap-2">
                        <Phone class="h-3.5 w-3.5 text-gray-400" />
                        <span class="text-gray-500">Celular</span>
                        <span class="text-gray-900 font-medium">{{ phone }}</span>
                    </div>
                    <button>
                        <Copy class="h-3.5 w-3.5 text-gray-400 hover:text-gray-600" />
                    </button>
                </div>
                <div v-if="landline" class="flex items-center justify-between text-xs group">
                    <div class="flex items-center gap-2">
                        <Phone class="h-3.5 w-3.5 text-gray-400" />
                        <span class="text-gray-500">Telefone</span>
                        <span class="text-gray-900 font-medium">{{ landline }}</span>
                    </div>
                    <button>
                        <Copy class="h-3.5 w-3.5 text-gray-400 hover:text-gray-600" />
                    </button>
                </div>
                <div v-if="email" class="flex items-center justify-between text-xs group">
                    <div class="flex items-center gap-2 flex-1 min-w-0">
                        <Mail class="h-3.5 w-3.5 text-gray-400 shrink-0" />
                        <span class="text-gray-500 shrink-0">E-mail</span>
                        <span class="text-gray-900 font-medium truncate">{{ email }}</span>
                    </div>
                    <button>
                        <Copy class="h-3.5 w-3.5 text-gray-400 hover:text-gray-600" />
                    </button>
                </div>
            </div>
        </CardContent>
    </Card>
</template>
