# Projeto: Vaga Corretor de Imóveis (recrutamento)

## REGRA FIXA: pesquisar antes de iniciar
Em QUALQUER solicitação sobre este projeto, antes de começar:
1. Ler este `CLAUDE.md`.
2. Ler a nota do Obsidian: `Cerebro-Claude/01-Projetos/Vaga Corretor/Projeto - Vaga Corretor.md`.
3. Ler a memória do projeto (Claude) sobre a vaga.
Antes de alterar ou publicar: atualizar a nota do Obsidian e a memória. Depois: registrar o que mudou.

## O que é
Local da vaga: NITERÓI E RIO DE JANEIRO (alterado em 03/11/2026, antes era Centro - RJ).
Página de recrutamento "Estamos contratando: Vendedor / Corretor de Imóvel" no visual do flyer
(fundo preto→cinza, painel azul #062E6E, foto do Aritan à direita).
O painel azul tem barra de rolagem própria com: Requisitos, Benefícios e o formulário de inscrição.

## Layout responsivo (03/11/2026)
- Computador (>860px): títulos e painel azul na coluna esquerda, foto grande na direita, "SAIBA MAIS..." leva ao formulário. Tamanhos dos títulos se ajustam à altura da tela (vh) para o painel sempre ter espaço.
- Celular/tablet (<=860px): títulos no topo, foto ao lado de "Vendedor" e POR CIMA das letras "CONTRATANDO" (z-index 4; painel azul z-index 5 fica sobre a base da foto), painel azul ocupa o resto da tela com rolagem própria.
- Telas baixas (<=560px de altura, celular deitado): a página rola inteira, sem rolagem interna.
- Testado em 1920x1080, 1366x768, 1280x720, iPad em pé e deitado, iPhone SE, iPhone 13 e Galaxy.

## Formulário
SÓ E-MAIL (decisão do Aritan, 03/11/2026): a página NÃO envia mais para o Google Forms. Os entry IDs abaixo ficam só como referência dos campos (os inputs usam esses `name`).
Google Forms original (desligado):
`https://docs.google.com/forms/d/e/1FAIpQLSf-r8f2DFkVQgGLUg5H0P4COv4rV8xvl6BCLwrMBYkltv7oBQ/formResponse`

| Pergunta | entry | Obrigatória |
|---|---|---|
| Seu nome completo? | entry.243228665 | sim |
| Sua data de nascimento? | entry.1183170890 | não |
| Telefone (WhatsApp) | entry.1969745615 | sim |
| CEP | entry.96283891 | não (ViaCEP preenche o endereço) |
| Endereço | entry.884526706 | não |
| Começar imediatamente? (Sim/Não) | entry.1982846341 | não |
| Anos de experiência com VENDAS | entry.844598664 | não |
| Tem CRECI? (SIM/NÃO) | entry.121096117 | sim |
| Registro no CRECI (só aparece se SIM) | entry.1868316806 | não |
| Disponibilidade (Integral/Manhã/Tarde) | entry.294540504 | sim |

**E-mail do cadastro (03/11/2026, versão atual): Netlify Forms.** O formulário oculto `candidatura` (data-netlify) é detectado no deploy; o JS faz POST urlencoded para `/` com `form-name=candidatura`. A notificação por e-mail para imoveisjornada@gmail.com é configurada no Netlify (Project configuration > Notifications > Form submission notifications). FormSubmit foi REMOVIDO (não entregava).
**REGRA do Aritan:** cadastro de candidato NÃO vai para planilha de LEADS/ACOMPANHAMENTO nem nenhuma outra planilha nova; só e-mail. Não mexer no Apps Script LEADS por causa desta página.

Se alguma pergunta mudar no Google Forms, atualizar o `name` do input correspondente.
Após enviar: mensagem de agradecimento do formulário + botão WhatsApp (21) 95943-4519 com o primeiro nome.

## Política de Privacidade (03/11/2026)
`privacidade.html` (LGPD): controlador Aritan Nakia Moreira Cordeiro / Aritan Especialista, contato imoveisjornada@gmail.com. Link no aviso de consentimento abaixo do botão de envio e no fim do painel azul. Retenção 12 meses. Cita compartilhamento com Netlify, GA4, Meta e a construtora parceira da vaga.

## Stack
HTML/CSS/JS estático, arquivo único `index.html`. Fontes self-hosted em `fonts/` (Bebas Neue + Poppins).
Foto: `img/aritan.webp` (+ `aritan.png` fallback), recorte sem fundo.

## Mensuração
- GA4 `G-2GEJSERC6B`: eventos `inicio_candidatura`, `candidatura_vaga`, `clique_whatsapp` (origem vaga).
- Meta Pixel `1902592370422998`: PageView + `CandidaturaVaga` (custom, NÃO usa Lead para não sujar campanhas de imóveis).

## Repositório e publicação
- GitHub: https://github.com/jorn4da/vaga (branch main)
- Pasta local: `~/Claude/Projects/Programador | SITE E LANDING PAGE/vaga`
- Publicar: `PUBLICAR-VAGA.command` (commit + push). Hospedagem: conectar o repo no Netlify ou GitHub Pages.
