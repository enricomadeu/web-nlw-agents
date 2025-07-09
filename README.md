# NLW Agents

Frontend do projeto **NLW Agents**, um projeto desenvolvido durante o evento da Rocketseat. O objetivo é demonstrar conceitos modernos de desenvolvimento front-end com React, gerenciamento de estado, rotas, estilização utilitária e boas práticas de componentização.

## ✨ Tecnologias e Bibliotecas

- **[React 19](https://react.dev/)** – Biblioteca principal para construção da interface.
- **[React Router DOM 7](https://reactrouter.com/)** – Gerenciamento de rotas SPA.
- **[@tanstack/react-query](https://tanstack.com/query/latest)** – Gerenciamento de dados assíncronos, cache e sincronização de estado do servidor.
- **[Tailwind CSS 4](https://tailwindcss.com/)** – Utilitário para estilização rápida e responsiva.
- **[class-variance-authority](https://cva.style/)** e **[clsx](https://github.com/lukeed/clsx)** – Utilitários para composição dinâmica de classes CSS.
- **[Radix UI](https://www.radix-ui.com/)** – Componentes acessíveis e primitives.
- **[Lucide React](https://lucide.dev/)** – Ícones SVG.
- **[TypeScript](https://www.typescriptlang.org/)** – Tipagem estática para maior segurança e produtividade.

## 🗂️ Estrutura do Projeto

```
src/
  components/      # Componentes reutilizáveis (ex: UI/Button)
    ui/
      button.tsx
  pages/           # Páginas da aplicação (rotas)
    create-room.tsx
    room.tsx
  lib/             # Funções utilitárias e helpers
    utils.ts
  app.tsx          # Componente principal da aplicação
  main.tsx         # Ponto de entrada da aplicação
  index.css        # Estilos globais (Tailwind)
```

## 🏛️ Padrões de Projeto

- **Componentização**: Componentes reutilizáveis, desacoplados e com variantes (ex: botão com cva).
- **Pages**: Cada rota possui um componente em `src/pages`.
- **Hooks e React Query**: Uso de hooks para requisições e cache de dados.
- **Estilização utilitária**: Tailwind CSS e utilitários para composição de classes.
- **Separação de utilitários**: Funções auxiliares em `src/lib`.
- **Provider Pattern**: Uso de providers para contexto global (ex: QueryClientProvider).

## ⚙️ Setup e Configuração

### 1. Clone o repositório

```bash
git clone <url-do-repo>
cd web-nlw-agents
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Rode o projeto em modo desenvolvimento

```bash
npm run dev
```

Acesse em [http://localhost:5173](http://localhost:5173)

## 🛠️ Comandos Úteis

- `npm run dev` – Inicia o servidor de desenvolvimento.
- `npm run build` – Gera a build de produção.
- `npm run preview` – Visualiza a build de produção localmente.

## 📦 Requisitos

- Node.js 18+
- npm 9+

## 📚 Mais informações

- [Documentação do Vite](https://vitejs.dev/)
- [Documentação do Tailwind CSS](https://tailwindcss.com/docs)
- [Documentação do React Query](https://tanstack.com/query/latest/docs/framework/react/overview)

---

Projeto desenvolvido durante o evento **NLW Agents da Rocketseat** 🚀

---
