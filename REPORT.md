# A11y Verification Report — Página da política de privacidade

Relatório da página estática `index.html` (política de privacidade do XC BK Teclado Braille Keyboard), publicada no GitHub Pages como o endereço público exigido pela Google Play. Desde 24/11/2026 ela é gerada por `site-xcbk/montar.mjs` a partir de `site-xcbk/paginas/privacidade.html`, o mesmo texto da página Privacidade do site do XC BK.

> Este relatório é um registro versionado do projeto.

## 📌 Contexto da Validação
- **Funcionalidade/Épico:** Página pública da política de privacidade (uma página, só leitura, sem script, sem formulário, sem mídia)
- **Data do Teste:** 24/11/2026
- **Cobre a interface em:** `index.html` com sha256 e84a3112ee3e934054bd83a608d33b312317570e46ebd1ae6b23fd4f95305024
- **Versão do padrão:** 2.2.0
- **Perfil de conformidade:** Shield (AAA), o mesmo do aplicativo
- **Status de Conformidade:** ⚠️ CONDICIONAL (faltam o teste com leitor de tela, o axe/Lighthouse e a verificação independente)
- **Independência da Verificação:** self-reported — verificou: Claude Code (Opus 5.5), a mesma sessão que escreveu a página
- **Gate estático (`verify-a11y.py`):** PASS (0 erros, 1 aviso: a verificação é self-reported, o que limita o status a CONDICIONAL) — rodado em: 24/11/2026

## 1. Verificação Técnica (Automated & Semantics)
- [ ] **Axe-Core / Lighthouse:** não rodado — esta sessão não tem axe nem Lighthouse. Quem deve rodar: uma sessão nova com navegador, ou Alexandre.
- [x] **Semântica HTML:** lido no código — `header`, `main`, `footer`, `h1`, `h2`, `p`, `ul`/`li` (com uma lista dentro de outra), `strong`, links `a`. Sem `div` ou `span` interativos, sem ARIA, sem script.
- [x] **Hierarquia de Títulos (H1-H6):** lido no código — um `h1` e vários `h2`, sem saltos.
- [x] **Idioma e título (SC 3.1.1, 2.4.2):** `<html lang="pt-BR">` e `<title>` com o tema da página, parte específica primeiro. O link para a política da Google leva `hl=pt-BR`.

## 2. Tab Order e Focus Management
- [x] **Indicador de Foco:** lido no CSS — `a:focus-visible` com contorno de 3 px na cor do link (10,04:1 no tema claro, 11,04:1 no escuro); nenhum `outline: none`.
- [x] **Navegação Lógica:** lido no código — três paradas de Tab (o link da política da Google, o e-mail em "Seus direitos" e o e-mail do rodapé), na ordem visual.
- [x] **Foco Capturado (Modals/Overlays):** N/A — sem modal.

## 3. Comportamento e Retorno de Tarefas
- [ ] **Screen Reader Test:** não executado por esta sessão. Quem deve executar: Alexandre, com o leitor de tela e o navegador que usa no computador (registrar o par aqui).
  - Par(es) usado(s): [pendente]
  - Quem executou e quando: [pendente]
  - Cenários executados: ler a página inteira por títulos; chegar aos links.
- [~] **Controle por Voz:** lido no código — os links não têm `aria-label`; o nome de cada um é o texto visível. Não testado com ferramenta de voz.
- [x] **Estados interativos inventariados:** só links (normal e com foco), lidos no código; sem menu, diálogo, validação ou carregamento.
- [x] **Mudança de Status (`aria-live`):** N/A — nada muda na página.
- [x] **Preenchimento de Formulários:** N/A — sem formulário.

## 4. Percepção Visual e Compreensão
- [x] **Contraste de Texto & UI:** pares medidos com `tools/contrast-check.py --profile shield` em 24/11/2026.
  | Par | Primeiro plano | Fundo | Razão | Piso | Resultado |
  | :--- | :--- | :--- | ---: | ---: | :--- |
  | claro: texto corrido e títulos | #1a1a1a | #ffffff | 17.40:1 | 7.0:1 | ✅ |
  | claro: link e anel de foco | #0b3d91 | #ffffff | 10.04:1 | 7.0:1 | ✅ |
  | claro: data da atualização | #4a4a4a | #ffffff | 8.86:1 | 7.0:1 | ✅ |
  | escuro: texto corrido e títulos | #f0f0f0 | #121212 | 16.44:1 | 7.0:1 | ✅ |
  | escuro: link e anel de foco | #a8c8ff | #121212 | 11.04:1 | 7.0:1 | ✅ |
  | escuro: data da atualização | #c8c8c8 | #121212 | 11.20:1 | 7.0:1 | ✅ |
- [x] **Redundância:** links sublinhados, não dependem só da cor.
- [~] **Scale / Zoom:** lido no CSS — tamanhos em `rem`, largura máxima de `80ch`, sem altura fixa, sem `overflow` escondido, `viewport` sem bloqueio de zoom. O mesmo CSS foi conferido a 320 px no site do XC BK (ver `site-xcbk/REPORT.md`); esta página em si não foi aberta a 200% nem a 320 px.
- [x] **Tipografia (regras da casa):** fonte de 18 px, entrelinha 1,6, espaço depois do parágrafo de 2,25 rem (2× a fonte), alinhado ao início, sem justificar.

## 5. Mídia Temporal e Movimento
N/A — sem mídia temporal.

## 6. Carga Cognitiva e Fluxo
N/A — página de uma etapa, sem autenticação nem limite de tempo. Linguagem simples, frases curtas; a única sigla técnica (SHA-256) vem explicada como "resumo cifrado".

---
## 📝 Notas de Avaliação ou Bloqueios Conhecidos
- **Nota 1:** o verificador é o mesmo agente que escreveu a página, então o teto é CONDICIONAL.
- **Nota 2:** a validação humana com leitor de tela continua obrigatória e é de Alexandre.
- **Nota 3:** a versão de 05/11/2026 dizia que o aplicativo não usava internet; foi substituída em 24/11/2026 porque a edição com planos (0.12.1) usa a internet para conferir compras.
