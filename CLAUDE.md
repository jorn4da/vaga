# Projeto: Vaga Corretor de Imóveis (recrutamento)

## REGRA FIXA: pesquisar antes de iniciar
Em QUALQUER solicitação sobre este projeto, antes de começar:
1. Ler este `CLAUDE.md`.
2. Ler a nota do Obsidian: `Cerebro-Claude/01-Projetos/Vaga Corretor/Projeto - Vaga Corretor.md`.
3. Ler a memória do projeto (Claude) sobre a vaga.
Antes de alterar ou publicar: atualizar a nota do Obsidian e a memória. Depois: registrar o que mudou.

## O que é
Página de recrutamento "Estamos contratando: Vendedor / Corretor de Imóvel" no visual do flyer
(fundo preto→cinza, painel azul #062E6E, foto do Aritan à direita).
O painel azul tem barra de rolagem própria com: Requisitos, Benefícios e o formulário de inscrição.

## Layout responsivo (03/11/2026)
- Computador (>860px): títulos e painel azul na coluna esquerda, foto grande na direita, "SAIBA MAIS..." leva ao formulário. Tamanhos dos títulos se ajustam à altura da tela (vh) para o painel sempre ter espaço.
- Celular/tablet (<=860px): títulos no topo, foto menor ao lado de "Vendedor", painel azul ocupa o resto da tela com rolagem própria.
- Telas baixas (<=560px de altura, celular deitado): a página rola inteira, sem rolagem interna.
- Testado em 1920x1080, 1366x768, 1280x720, iPad em pé e deitado, iPhone SE, iPhone 13 e Galaxy.

## Formulário
As respostas vão direto para o Google Forms original (mesma planilha de respostas):
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

**Cópia por e-mail (03/11/2026):** cada cadastro também é enviado para imoveisjornada@gmail.com via FormSubmit (`https://formsubmit.co/ajax/imoveisjornada@gmail.com`, variável `EMAIL_URL`), assunto "Novo cadastro | Vaga Corretor de Imóveis | Nome", com todas as respostas em tabela + link direto do WhatsApp. Os dois envios (Forms e e-mail) rodam juntos; o candidato espera no máximo 6s.
Se for o primeiro envio deste site, o FormSubmit pode mandar um e-mail de ativação: clicar em "Activate Form".

Se alguma pergunta mudar no Google Forms, atualizar o `name` do input correspondente.
Após enviar: mensagem de agradecimento do formulário + botão WhatsApp (21) 95943-4519 com o primeiro nome.

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
