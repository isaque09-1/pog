# PET Manager

Plataforma web para emissão e acompanhamento de Permissões de Entrada e Trabalho (PET) e Permissões de Trabalho (PT).

## Desenvolvimento

```bash
pnpm install --frozen-lockfile --ignore-scripts
pnpm run dev
```

O build de produção é gerado em `dist/`:

```bash
pnpm install --frozen-lockfile --ignore-scripts
./node_modules/.bin/vite build
```

## Estado atual

O frontend está publicado no Cloudflare Pages, mas os dados ainda são demonstrativos e vivem em memória no navegador. O app ainda não deve ser usado com dados reais de clientes.

Antes da primeira operação real, é necessário implementar:

- autenticação e recuperação de acesso;
- organizações e isolamento multiempresa;
- persistência de PETs, PTs, rondas, assinaturas e encerramentos;
- Row Level Security no banco;
- trilha de auditoria;
- checklists de PT validados pelo responsável de Segurança do Trabalho;
- backups, monitoramento e política de retenção.

## Arquitetura de produção planejada

```text
React + Vite -> Cloudflare Pages -> Supabase Auth/PostgreSQL
```

O frontend deve acessar o banco somente através de políticas RLS. A chave `service_role` nunca deve ser colocada no frontend.
