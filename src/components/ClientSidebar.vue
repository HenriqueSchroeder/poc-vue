<script setup lang="ts">
import { Badge } from './ui/badge'
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from './ui/accordion'
import { Phone, Mail, Copy, Plus } from 'lucide-vue-next'

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
    <aside class="w-80">
        <div class="bg-white border-r min-h-screen">
            <!-- Cliente Section -->
            <div class="p-6 border-b">
                <Badge variant="outline" class="mb-4">Cliente</Badge>

                <div class="space-y-4">
                    <div>
                        <h3 class="font-semibold text-gray-900 text-sm leading-tight">{{ companyName }}</h3>
                        <p class="text-xs text-gray-500 mt-1">{{ companySubtitle }}</p>
                    </div>

                    <div>
                        <h4 class="font-semibold text-gray-900 text-sm">{{ contactName }}</h4>
                        <p class="text-xs text-gray-500 mt-0.5">{{ contactRole }}</p>
                    </div>

                    <div class="space-y-2">
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
                </div>
            </div>

            <!-- Vendas Realizadas Section -->
            <div class="p-6 border-b">
                <Accordion type="single" collapsible>
                    <AccordionItem value="vendas" class="border-0">
                        <AccordionTrigger class="p-0 hover:no-underline">
                            <span class="text-sm font-medium text-gray-700">Vendas realizadas</span>
                        </AccordionTrigger>
                        <AccordionContent class="pt-4">
                            <div class="space-y-3">
                                <div>
                                    <div class="text-xs text-gray-500 mb-1">Total vendido</div>
                                    <div class="text-lg font-semibold text-gray-900">R$ 523,00</div>
                                </div>
                                <button
                                    class="w-full py-2 px-3 border border-gray-300 rounded text-sm text-gray-700 hover:bg-gray-50 flex items-center justify-center gap-2">
                                    <Plus class="h-4 w-4" />
                                    Vincular pedido
                                </button>
                                <div class="border-t pt-3">
                                    <div class="text-xs text-gray-500 mb-2">Valor líquido</div>
                                    <div class="text-2xl font-bold text-green-600">R$ 2500,00</div>
                                    <div class="grid grid-cols-3 gap-2 mt-3 text-xs">
                                        <div>
                                            <div class="text-gray-500">Lucro bruto</div>
                                            <div class="font-semibold">R$500,00</div>
                                        </div>
                                        <div>
                                            <div class="text-gray-500">Margem</div>
                                            <div class="font-semibold">10%</div>
                                        </div>
                                        <div>
                                            <div class="text-gray-500">Qdte de itens</div>
                                            <div class="font-semibold">45</div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </AccordionContent>
                    </AccordionItem>
                </Accordion>
            </div>

            <!-- Exemplo de campo Section -->
            <div class="p-6 border-b">
                <Accordion type="single" collapsible>
                    <AccordionItem value="campos" class="border-0">
                        <AccordionTrigger class="p-0 hover:no-underline">
                            <span class="text-sm font-medium text-gray-700">Exemplo de campo</span>
                        </AccordionTrigger>
                        <AccordionContent class="pt-4">
                            <div class="space-y-3">
                                <div class="flex items-center gap-2">
                                    <div class="h-10 w-10 rounded-full bg-gray-300" />
                                    <span class="text-sm text-gray-700">Exemplo de campo</span>
                                </div>
                                <div class="text-sm text-gray-600">Exemplo de campo 2</div>
                                <button class="text-sm text-gray-500 hover:text-gray-700">
                                    Exibir todos os campos etapa
                                </button>
                            </div>
                        </AccordionContent>
                    </AccordionItem>
                </Accordion>
            </div>

            <!-- Anexos Section -->
            <div class="p-6">
                <Accordion type="single" collapsible>
                    <AccordionItem value="anexos" class="border-0">
                        <AccordionTrigger class="p-0 hover:no-underline">
                            <span class="text-sm font-medium text-gray-700">Anexos</span>
                        </AccordionTrigger>
                        <AccordionContent class="pt-4">
                            <p class="text-sm text-gray-500">Nenhum anexo</p>
                        </AccordionContent>
                    </AccordionItem>
                </Accordion>
            </div>
        </div>
    </aside>
</template>
