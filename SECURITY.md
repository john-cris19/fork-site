# Política de segurança

Testes de segurança neste site são bem-vindos. Ele é estático e não tem login nem banco de dados.

## No escopo
- O site em https://fork-community.pages.dev (inclui /painel, /entrar e /api/*).
- O código deste repositório: build, workflow e pós-build.

## Fora do escopo
- O servidor do Discord, os bots (Forkito, Yara) e contas de membros.
- A infraestrutura do GitHub.
- Ataques de negação de serviço, engenharia social e spam.

## Como reportar
Abra um **aviso privado** em *Security → Report a vulnerability* neste repositório, ou fale com a staff por ticket no Discord.
Não abra issue pública com detalhes de uma falha antes da correção.

## O que já está no site
- Content-Security-Policy com hash por script e sem `unsafe-inline` em scripts.
- Proteção contra iframe: o GitHub Pages não permite o header `frame-ancestors`, então a página se esconde por script quando é aberta dentro de um iframe.
- `Referrer-Policy: strict-origin-when-cross-origin`.
- Nenhum segredo no front-end. O build verifica isso automaticamente.
- Parâmetros de URL validados contra uma lista fechada de valores.
- Dependências auditadas no CI e atualizadas pelo Dependabot.
- Actions do GitHub fixadas por SHA, com permissões mínimas.

## Limitações conhecidas (GitHub Pages)
- Não dá para enviar headers HTTP próprios: HSTS customizado, `X-Frame-Options`, `frame-ancestors` e CSP por header.
- `style-src` aceita `'unsafe-inline'` por causa de atributos `style` com variáveis CSS. Isso não executa código.
