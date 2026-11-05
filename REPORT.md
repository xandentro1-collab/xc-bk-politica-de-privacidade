# A11y Verification Report — Página da política de privacidade

Relatório da página estática `index.html` (política de privacidade do XC BK Teclado Braille Keyboard), publicada para servir de endereço público exigido pela Google Play.

> Este relatório é um registro versionado do projeto.

## 📌 Contexto da Validação
- **Funcionalidade/Épico:** Página pública da política de privacidade (uma página, só leitura, sem script, sem formulário, sem mídia)
- **Data do Teste:** 05/11/2026
- **Cobre a interface em:** `index.html` com sha256 e0382ac7f4f9fdf2e364dcc038a4dc6792ff2461d5e958ebc4ea8772eaf762cb
- **Versão do padrão:** 2.2.0
- **Perfil de conformidade:** Standard (AA), com contraste e tamanhos já no nível Shield
- **Status de Conformidade:** ⚠️ CONDICIONAL (faltam o teste com leitor de tela e o teste de zoom no navegador)
- **Independência da Verificação:** self-reported — verificou: Claude Code (Sonnet 5.5), a mesma sessão que escreveu a página
- **Gate estático (`verify-a11y.py`):** PASS (0 erros, 1 aviso: a verificação é self-reported, o que limita o status a CONDICIONAL) — rodado em: 05/11/2026

## 1. Verificação Técnica (Automated & Semantics)
- [ ] **Axe-Core / Lighthouse:** não rodado — esta sessão não executou axe nem Lighthouse. Quem deve rodar: Alexandre ou uma sessão nova com navegador.
- [x] **Semântica HTML:** lido no código — `header`, `main`, `footer`, `h1`, `h2`, `p`, `ul`/`li`, um único `a`. Sem `div` ou `span` interativos, sem ARIA.
- [x] **Hierarquia de Títulos (H1-H6):** lido no código — um `h1` e vários `h2`, sem saltos.
- [x] **Idioma e título (SC 3.1.1, 2.4.2):** `<html lang="pt-BR">` e `<title>` com o tema da página, parte específica primeiro.

## 2. Tab Order e Focus Management
- [x] **Indicador de Foco:** lido no CSS — `a:focus-visible` com contorno de 3 px na cor do link (#0b3d91 sobre #ffffff, 10,04:1); nenhum `outline: none`.
- [x] **Navegação Lógica:** a página tem uma única parada de Tab (o link do e-mail, no fim), na ordem visual.
- [x] **Foco Capturado (Modals/Overlays):** N/A — sem modal.

## 3. Comportamento e Retorno de Tarefas
- [ ] **Screen Reader Test:** não executado por esta sessão. Quem deve executar: Alexandre, com o leitor de tela e o navegador que usa no computador (registrar o par aqui).
  - Par(es) usado(s): [pendente]
  - Quem executou e quando: [pendente]
  - Cenários executados: ler a página inteira por títulos; chegar ao link do e-mail.
- [~] **Controle por Voz:** lido no código — o único controle é um link cujo texto visível é o próprio endereço de e-mail, e não há `aria-label`; não testado com ferramenta de voz.
- [x] **Estados interativos inventariados:** só existe o link (normal e com foco), ambos lidos no código; sem menu, diálogo, validação ou carregamento.
- [x] **Mudança de Status (`aria-live`):** N/A — nada muda na página.
- [x] **Preenchimento de Formulários:** N/A — sem formulário.

## 4. Percepção Visual e Compreensão
- [x] **Contraste de Texto & UI:** pares medidos com `tools/contrast-check.py --profile shield`.
  | Par | Primeiro plano | Fundo | Razão | Piso | Resultado |
  | :--- | :--- | :--- | ---: | ---: | :--- |
  | texto corrido e títulos | #1a1a1a | #ffffff | 17.40:1 | 7.0:1 | ✅ |
  | link e anel de foco | #0b3d91 | #ffffff | 10.04:1 | 7.0:1 | ✅ |
- [x] **Redundância:** o link é sublinhado, não depende só da cor.
- [~] **Scale / Zoom:** lido no CSS — tamanhos em `rem`, largura máxima de `80ch`, sem altura fixa, sem `overflow` escondido, `viewport` sem bloqueio de zoom. Não conferido a 200% e a 320 px num navegador.
- [x] **Tipografia (regras da casa):** fonte de 18 px (1,125 rem), entrelinha 1,6, espaço depois do parágrafo de 1,25 rem, texto alinhado à esquerda, sem justificar.

## 5. Mídia Temporal e Movimento
N/A — sem mídia temporal.

## 6. Carga Cognitiva e Fluxo
N/A — página de uma etapa, sem autenticação nem limite de tempo. Linguagem simples, frases curtas, sem sigla sem explicação.

---
## 📝 Notas de Avaliação ou Bloqueios Conhecidos
- **Nota 1:** o verificador é o mesmo agente que escreveu a página, então o teto é CONDICIONAL.
- **Nota 2:** a validação humana com leitor de tela continua obrigatória e é de Alexandre.
