# Site — Barbearia do Prado

Site institucional e sistema de agendamento online da Barbearia do Prado (Chapecó - SC), com painel administrativo para o barbeiro Prado.

## O que está incluído

Um único arquivo autocontido: **`index.html`** (HTML + CSS + JavaScript puro, sem build, sem dependências de instalação). Ele contém:

- Site público (Sobre, Serviços, O Prado, Localização, WhatsApp, mapa)
- Fluxo de agendamento online (serviço → data/horário → dados → confirmação)
- Reconhecimento de cliente recorrente pelo telefone
- Painel administrativo protegido por login (e-mail + senha com hash), com:
  - Dashboard (próximo cliente, contadores do dia)
  - Minha Agenda (cards de agendamento, filtros rápidos, busca)
  - Agendamentos, Serviços, Clientes, Horários de funcionamento, Configurações

## ⚠️ Limitação técnica importante

Este projeto foi desenvolvido dentro do ambiente de chat da Claude (Anthropic), que oferece um recurso de **armazenamento próprio do ambiente** (`window.storage`) para simular um banco de dados — já que esse ambiente não tem acesso a internet para configurar um backend/servidor real.

Isso significa que, **hospedado como está** (por exemplo, no GitHub Pages, Netlify, Vercel como site estático, etc.), o visual do site funciona normalmente, mas:

- O agendamento **não vai salvar dados de verdade**;
- O login do painel administrativo **não vai funcionar** (`window.storage` não existe fora do ambiente da Claude).

### Para colocar em produção de verdade

Antes de divulgar este site para clientes reais, ele precisa de um backend simples que substitua o `window.storage` por chamadas de API para um banco de dados real (por exemplo: Supabase, Firebase, ou uma API própria em Node/Express + PostgreSQL). A lógica de agendamento, disponibilidade de horários e regras de negócio já está toda pronta no `index.html` — o trabalho que falta é trocar as poucas funções que leem/gravam em `window.storage` (`loadDB` e `saveDB`) por chamadas ao backend escolhido.

Enquanto isso, o repositório serve como:
- Portfólio/demonstração visual do projeto;
- Protótipo funcional para apresentar ao cliente (com dados de teste feitos ao vivo);
- Base de código pronta para a próxima etapa (integração com backend real).

## Como rodar localmente

Não precisa de nenhuma instalação. Basta abrir o `index.html` num navegador, ou rodar um servidor local simples:

```bash
npx serve .
# ou
python3 -m http.server 8000
```

## Publicar com GitHub Pages (visual apenas, sem dados reais)

1. No repositório, vá em **Settings → Pages**.
2. Em "Source", selecione a branch `main` e a pasta `/ (root)`.
3. Salve. O GitHub vai gerar uma URL pública (algo como `https://SEU-USUARIO.github.io/site-barbearia/`) em alguns minutos.

## Serviços e informações reais já configurados

- Endereço: Rua Marechal Deodoro, 655, Jardim Itália, Chapecó - SC, 89802-272
- WhatsApp: (49) 98885-1058
- Horários: Segunda 13:30–19:30 · Terça a sexta 09:00–12:00 e 13:30–19:30 · Sábado 09:00–17:00 · Domingo fechado
- Serviços: Cabelo, Barba, Barba + Cabelo, Depilação nariz/orelha, Máquina geral (Pente 1), Pigmentação da barba, Sobrancelha
