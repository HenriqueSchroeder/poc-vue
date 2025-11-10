<script setup lang="ts">
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from './ui/accordion'
import CustomField from './CustomField.vue'
</script>

<template>
  <aside class="w-80">
    <div class="bg-white border-l min-h-screen">
      <!-- Campos da etapa Section -->
      <div class="p-6 border-b">
        <Accordion type="single" collapsible>
          <AccordionItem value="campos-etapa" class="border-0">
            <AccordionTrigger class="p-0 hover:no-underline">
              <span class="text-sm font-medium text-gray-700">Campos da etapa</span>
            </AccordionTrigger>
            <AccordionContent class="pt-4">
              <div class="space-y-1">
                <CustomField label="Label" />
                <CustomField label="Label" expanded />
              </div>
            </AccordionContent>
          </AccordionItem>
        </Accordion>
      </div>

      <!-- Financeiro Section -->
      <div class="p-6 border-b">
        <Accordion type="single" collapsible>
          <AccordionItem value="financeiro" class="border-0">
            <AccordionTrigger class="p-0 hover:no-underline">
              <span class="text-sm font-medium text-gray-700">Financeiro</span>
            </AccordionTrigger>
            <AccordionContent class="pt-4">
              <p class="text-sm text-gray-500">Sem informações financeiras</p>
            </AccordionContent>
          </AccordionItem>
        </Accordion>
      </div>

      <!-- Classificação gestões ativos Section -->
      <div class="p-6 border-b">
        <Accordion type="single" collapsible>
          <AccordionItem value="classificacao" class="border-0">
            <AccordionTrigger class="p-0 hover:no-underline">
              <span class="text-sm font-medium text-gray-700">Classificação gestões ativos</span>
            </AccordionTrigger>
            <AccordionContent class="pt-4">
              <p class="text-sm text-gray-500">Sem classificações</p>
            </AccordionContent>
          </AccordionItem>
        </Accordion>
      </div>

      <!-- Histórico e potencial do cliente Section -->
      <div class="p-6 border-b">
        <Accordion type="single" collapsible>
          <AccordionItem value="historico" class="border-0">
            <AccordionTrigger class="p-0 hover:no-underline">
              <span class="text-sm font-medium text-gray-700">Histórico e potencial do cliente</span>
            </AccordionTrigger>
            <AccordionContent class="pt-4">
              <p class="text-sm text-gray-500">Sem histórico</p>
            </AccordionContent>
          </AccordionItem>
        </Accordion>
      </div>

      <!-- Clientes ativos próximos Section -->
      <div class="p-6">
        <Accordion type="single" collapsible>
          <AccordionItem value="clientes-proximos" class="border-0">
            <AccordionTrigger class="p-0 hover:no-underline">
              <span class="text-sm font-medium text-gray-700">Clientes ativos próximos</span>
            </AccordionTrigger>
            <AccordionContent class="pt-4">
              <p class="text-sm text-gray-500">Sem clientes próximos</p>
            </AccordionContent>
          </AccordionItem>
        </Accordion>
      </div>
    </div>
  </aside>
</template>
