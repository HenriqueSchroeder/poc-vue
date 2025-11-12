# POC Vue - Sistema de Gestão de Negócios

Prova de conceito desenvolvida com Vue 3, TypeScript e Vite, implementando um sistema de gestão de negócios com interface moderna e componentes reutilizáveis.

## 🚀 Tecnologias

- **Vue 3** - Framework JavaScript progressivo
- **TypeScript** - Superset tipado do JavaScript
- **Vite** - Build tool e dev server de alta performance
- **Tailwind CSS** - Framework CSS utility-first
- **Reka UI** - Componentes Vue acessíveis e sem estilo
- **Lucide Vue Next** - Ícones modernos para Vue
- **VueUse** - Coleção de utilitários composables para Vue

## 📦 Funcionalidades

Este projeto implementa uma interface completa de gestão de negócios com:

- **Dashboard de Negociações**: Visualização e gerenciamento de deals
- **Gestão de Clientes**: Sidebar com informações detalhadas de clientes
- **Controle de Etapas**: Acompanhamento do progresso das negociações
- **Sistema de Atividades**: Lista e gerenciamento de tarefas
- **Histórico Completo**: Registro de todas as interações e mudanças
- **Notas e Comentários**: Sistema de anotações integrado
- **Componentes UI**: Biblioteca de componentes reutilizáveis

## 🎨 Componentes

### Componentes de Negócio
- `DealHeader` - Cabeçalho de negociação
- `StageProgress` - Progresso das etapas
- `ClientCard` / `ClientSidebar` - Informações do cliente
- `StageSidebar` - Barra lateral de etapas
- `ActivityList` / `ActivityItem` - Lista de atividades
- `HistoryList` / `HistoryItem` - Histórico de eventos
- `NoteForm` - Formulário de notas

### Componentes UI Base
- Accordion
- Avatar
- Badge
- Button
- Calendar
- Card
- Input
- Popover
- Select
- Separator
- Tabs
- Textarea
- TimePicker

## 🛠️ Instalação

```bash
# Instalar dependências
yarn install

# Ou com npm
npm install
```

## 🔧 Scripts Disponíveis

```bash
# Iniciar servidor de desenvolvimento
yarn dev

# Build para produção
yarn build

# Preview da build de produção
yarn preview
```

## 📁 Estrutura do Projeto

```
poc-vue/
├── src/
│   ├── components/          # Componentes da aplicação
│   │   ├── ui/             # Componentes UI reutilizáveis
│   │   └── ...             # Componentes de negócio
│   ├── lib/                # Utilitários e helpers
│   ├── assets/             # Recursos estáticos
│   ├── App.vue             # Componente raiz
│   └── main.ts             # Entry point
├── public/                 # Arquivos públicos
└── ...                     # Arquivos de configuração
```

## 💻 Desenvolvimento

Este projeto utiliza:
- **Vue 3 `<script setup>`** para sintaxe de composição mais limpa
- **TypeScript** para tipagem estática e melhor IntelliSense
- **Tailwind CSS** para estilização rápida e consistente
- **Component-driven development** com componentes altamente reutilizáveis

## 📚 Recursos

- [Documentação do Vue 3](https://vuejs.org/)
- [Guia TypeScript do Vue](https://vuejs.org/guide/typescript/overview.html)
- [Documentação do Vite](https://vitejs.dev/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Reka UI](https://reka-ui.com/)

## 📄 Licença

Este projeto é privado e foi desenvolvido como prova de conceito.
