# 🥑 Avocato

Sistema de gestão para pequenas empresas de serviço: pedidos dos clientes, ordens de serviço, agenda da equipe, clientes, catálogo, financeiro e um assistente com IA gratuita, tudo em português e pronto para usar.

## O que ele faz

- **Link público de pedidos** (`/solicitar/sua-empresa`): o cliente pede o serviço sem criar conta; a empresa recebe notificação e a solicitação aparece nas OS.
- **Ordens de serviço** com itens, responsável, data, fluxo *solicitada → aberta → agendada → em andamento → concluída*, avaliação de 1 a 5 e aviso pelo WhatsApp.
- **Financeiro automático**: concluir uma OS (ou um atendimento da agenda) gera a conta a receber. Também tem despesas, parcelamento, contas fixas que se lançam sozinhas e baixa total ou parcial.
- **Agenda semanal** sem conflito de horário por profissional, com lembrete por WhatsApp.
- **Clientes** com histórico, etiquetas, "sumidos há 60 dias" e termos personalizáveis (Pacientes, Tutores…).
- **Serviços** com preço, custo, comissão, duração e margem calculada.
- **Equipe**: funcionários, freelancers e prestadores.
- **Painel** com recebido no mês, a receber/a pagar, fluxo de caixa de 12 meses e serviços mais vendidos.
- **Assistente IA** (Groq ou Google Gemini, ambos gratuitos) que consulta e registra no sistema. Ações sensíveis esperam aprovação humana.
- **Avatares ilustrados** que cada usuário monta do seu jeito (6 estilos, detalhes, cores, fundo).
- **Multiempresa** com isolamento por RLS no Postgres, papéis e permissões, e auditoria de tudo.

## Estrutura

```
avocato/
├── web/        Site (Next.js 16 + Tailwind) — o antigo Berry, agora Avocato
├── api/        API (Fastify + TypeScript) — regras de negócio e IA
├── supabase/   Migrations do banco + teste de isolamento
└── docs/       SETUP.md (passo a passo) e ARQUITETURA.md
```

O Supabase cuida do **login** e do **banco**. O site fala só com a API; a API fala com o banco usando um usuário próprio, sem poderes de administrador.

## Começando

Siga o **[docs/SETUP.md](docs/SETUP.md)**. Em resumo:

1. Crie um projeto no Supabase e aplique as migrations (`npx supabase db push`).
2. Crie o usuário `avocato_api` no SQL Editor.
3. Pegue uma chave grátis no Groq.
4. Rode a API (`api/`) e o site (`web/`) com os `.env` preenchidos.

## Testes

```bash
cd api
npm test        # unitários; os de integração rodam com TEST_DATABASE_URL (veja docs/SETUP.md)
```

## Créditos

Avatares gerados com [DiceBear](https://www.dicebear.com) (MIT). Estilos: Notionists e Lorelei (CC0), Adventurer e Big Smile e Micah (CC BY 4.0, de Lisa Wischofsky, Ashley Seo e Micah Lanier) e Avataaars (Pablo Stanley, uso livre). Ícones: Lucide. Fonte: Roboto (Fontsource).
