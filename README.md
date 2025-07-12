# Web NLW Agents

Interface web moderna desenvolvida em React para interação com IA, utilizando TypeScript, Vite, TailwindCSS e componentes shadcn/ui. Permite criar salas, fazer perguntas e gravar áudio para processamento inteligente.

## 🚀 Tecnologias Utilizadas

- **React 19** - Biblioteca para interfaces de usuário
- **TypeScript** - Superset do JavaScript com tipagem estática
- **Vite** - Build tool e dev server ultra rápido
- **TailwindCSS 4** - Framework CSS utility-first
- **shadcn/ui** - Componentes UI acessíveis e customizáveis
- **React Hook Form** - Gerenciamento de formulários performático
- **TanStack Query** - Gerenciamento de estado de servidor
- **React Router DOM** - Roteamento para SPA
- **Zod** - Validação de esquemas e tipagem
- **Lucide React** - Ícones modernos e consistentes

## 📋 Pré-requisitos

- Node.js 18+
- npm ou yarn
- Servidor backend em execução (server-nlw-agents)

## 🛠️ Instalação

1. **Clone o repositório:**

```bash
git clone https://github.com/enricomadeu/web-nlw-agents.git
cd web-nlw-agents
```

2. **Instale as dependências:**

```bash
npm install
```

3. **Configure o ambiente:**

Certifique-se de que o servidor backend esteja rodando em `http://localhost:3333`

4. **Inicie o projeto:**

```bash
npm run dev
```

O projeto estará disponível em `http://localhost:5173`

## 🚀 Scripts Disponíveis

- `npm run dev` - Inicia o servidor de desenvolvimento
- `npm run build` - Gera build de produção
- `npm run preview` - Visualiza o build de produção localmente

## 🌟 Funcionalidades

### 🏠 Página Inicial

- **Criar Salas**: Interface para criar novas salas de perguntas
- **Listar Salas**: Visualização de todas as salas disponíveis
- **Navegação Intuitiva**: Design limpo e responsivo

### 🎯 Sala de Perguntas

- **Formulário de Perguntas**: Interface para envio de perguntas
- **Lista de Perguntas**: Visualização de perguntas e respostas
- **Validação em Tempo Real**: Feedback instantâneo nos formulários
- **Estados de Loading**: Indicadores visuais de carregamento

### 🎙️ Gravação de Áudio

- **Gravação Contínua**: Captura de áudio em tempo real
- **Upload Automático**: Envio automático de chunks de áudio
- **Controles Intuitivos**: Interface simples para iniciar/parar gravação
- **Feedback Visual**: Indicadores de status da gravação

## 🏗️ Arquitetura do Projeto

```
src/
├── components/           # Componentes reutilizáveis
│   ├── ui/              # Componentes base (shadcn/ui)
│   │   ├── button.tsx
│   │   ├── card.tsx
│   │   ├── form.tsx
│   │   ├── input.tsx
│   │   ├── label.tsx
│   │   ├── textarea.tsx
│   │   └── badge.tsx
│   ├── create-room-form.tsx
│   ├── question-form.tsx
│   ├── question-item.tsx
│   ├── question-list.tsx
│   └── room-list.tsx
├── http/                # Lógica de API e tipos
│   ├── types/          # Tipos TypeScript para API
│   │   ├── create-room-request.ts
│   │   ├── create-room-response.ts
│   │   ├── create-question-request.ts
│   │   ├── create-question-response.ts
│   │   ├── get-rooms-response.ts
│   │   └── get-room-questions-response.ts
│   ├── use-create-room.ts
│   ├── use-create-question.ts
│   ├── use-rooms.ts
│   └── use-room-questions.ts
├── lib/                # Utilitários e configurações
│   ├── utils.ts        # Utilitários gerais
│   └── dayjs.ts        # Configuração de datas
├── pages/              # Páginas da aplicação
│   ├── create-room.tsx
│   ├── room.tsx
│   └── record-room-audio.tsx
├── app.tsx             # Componente principal e rotas
├── main.tsx            # Ponto de entrada da aplicação
└── index.css           # Estilos globais e tema
```

## 🎨 Design System

### Tema e Cores

- **Modo Dark**: Interface com tema escuro por padrão
- **Paleta Consistente**: Cores baseadas no design system do shadcn/ui
- **Variáveis CSS**: Sistema de cores flexível e customizável

### Componentes UI

- **shadcn/ui**: Componentes acessíveis e bem testados
- **Consistência Visual**: Design uniforme em toda aplicação
- **Responsividade**: Layout adaptável para diferentes telas

## 🔄 Gerenciamento de Estado

### TanStack Query

- **Cache Inteligente**: Cache automático de requisições
- **Sincronização**: Refetch automático quando necessário
- **Estados de Loading**: Gerenciamento de estados de carregamento
- **Otimistic Updates**: Atualizações otimistas para melhor UX

### React Hook Form

- **Performance**: Renderizações mínimas durante digitação
- **Validação**: Integração com Zod para validação tipada
- **UX**: Feedback em tempo real para usuários

## 🌐 Rotas

| Rota                  | Componente        | Descrição                                      |
| --------------------- | ----------------- | ---------------------------------------------- |
| `/`                   | `CreateRoom`      | Página inicial com criação e listagem de salas |
| `/room/:roomId`       | `Room`            | Sala de perguntas específica                   |
| `/room/:roomId/audio` | `RecordRoomAudio` | Interface de gravação de áudio                 |

## 📡 Integração com API

### Endpoints Utilizados

#### Salas

```typescript
// Listar salas
GET /rooms

// Criar sala
POST /rooms
{
  "name": "string",
  "description": "string"
}
```

#### Perguntas

```typescript
// Listar perguntas de uma sala
GET /rooms/:roomId/questions

// Criar pergunta
POST /rooms/:roomId/questions
{
  "question": "string"
}
```

#### Áudio

```typescript
// Upload de áudio
POST /rooms/:roomId/audio
Content-Type: multipart/form-data
```

## 🎙️ Funcionalidade de Áudio

### Recursos

- **MediaRecorder API**: Gravação nativa do navegador
- **Chunks Automáticos**: Divisão automática em intervalos de 5s
- **Upload Contínuo**: Envio automático durante gravação
- **Configuração Otimizada**:
  - Formato: WebM
  - Bitrate: 64kbps
  - Echo Cancellation: Ativado
  - Noise Suppression: Ativado

### Compatibilidade

- ✅ Chrome 47+
- ✅ Firefox 29+
- ✅ Safari 14+
- ✅ Edge 79+

## 🔧 Validação e Tipos

### Zod Schemas

```typescript
// Criação de sala
const createRoomSchema = z.object({
  name: z.string().min(3),
  description: z.string(),
});

// Criação de pergunta
const createQuestionSchema = z.object({
  question: z
    .string()
    .min(10, "Mínimo 10 caracteres")
    .max(500, "Máximo 500 caracteres"),
});
```

### Type Safety

- **Tipagem Completa**: Todos os dados tipados com TypeScript
- **Inferência Automática**: Tipos inferidos automaticamente dos schemas
- **Validação Runtime**: Validação em tempo de execução com Zod

## 🎯 Hooks Customizados

### API Hooks

- `useRooms()` - Busca lista de salas
- `useCreateRoom()` - Cria nova sala
- `useRoomQuestions(roomId)` - Busca perguntas de uma sala
- `useCreateQuestion(roomId)` - Cria nova pergunta

### Características

- **Auto-refetch**: Revalidação automática
- **Error Handling**: Tratamento de erros integrado
- **Loading States**: Estados de carregamento automáticos
- **Cache Management**: Gerenciamento inteligente de cache

## 📱 Responsividade

### Breakpoints

- **Mobile**: < 768px
- **Tablet**: 768px - 1024px
- **Desktop**: > 1024px

### Grid System

- **Layout Flexível**: Grid CSS e Flexbox
- **Componentes Adaptáveis**: UI que se adapta a diferentes telas
- **Touch Friendly**: Interfaces otimizadas para touch

## 🔄 Estados da Aplicação

### Loading States

- **Skeleton Loading**: Placeholders durante carregamento
- **Button Loading**: Estados de loading em botões
- **Form Submission**: Feedback durante envio de formulários

### Error Handling

- **Error Boundaries**: Captura de erros React
- **API Error Handling**: Tratamento de erros de API
- **User Feedback**: Feedback claro para usuários

## 🚀 Performance

### Otimizações

- **Code Splitting**: Divisão automática de código
- **Lazy Loading**: Carregamento sob demanda
- **Bundle Optimization**: Build otimizado com Vite
- **React Query Cache**: Cache inteligente de dados

### Métricas

- **Fast Refresh**: Hot reload instantâneo
- **Build Speed**: Build ultra rápido com Vite
- **Bundle Size**: Bundle otimizado para produção

## 🛠️ Desenvolvimento

### Padrões de Código

- **Component Composition**: Composição de componentes
- **Custom Hooks**: Lógica reutilizável em hooks
- **Type Safety**: Tipagem rigorosa com TypeScript
- **Clean Code**: Código limpo e legível

### Estrutura de Componentes

```typescript
// Exemplo de componente tipado
interface ComponentProps {
  title: string;
  onAction: () => void;
}

export function Component({ title, onAction }: ComponentProps) {
  return (
    <div className="component">
      <h1>{title}</h1>
      <button onClick={onAction}>Action</button>
    </div>
  );
}
```

## 🎨 Customização

### Tema

```css
/* Customização de cores no index.css */
:root {
  --primary: oklch(0.21 0.006 285.885);
  --background: oklch(1 0 0);
  /* ... outras variáveis */
}
```

### Componentes

- **Variant Props**: Variações de componentes com class-variance-authority
- **CSS Variables**: Sistema de cores flexível
- **TailwindCSS**: Utilitários para estilização rápida

## 🤝 Contribuindo

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📝 Licença

Este projeto não possui licença específica.

## 🔗 Links Úteis

- [React Documentation](https://react.dev/)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [Vite Guide](https://vitejs.dev/guide/)
- [TailwindCSS Documentation](https://tailwindcss.com/docs)
- [shadcn/ui Components](https://ui.shadcn.com/)
- [TanStack Query](https://tanstack.com/query/latest)
- [React Hook Form](https://react-hook-form.com/)
- [Zod Documentation](https://zod.dev/)

---

**Desenvolvido com ❤️ para o Next Level Week**
