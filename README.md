# LexScan Brasil

Analisador preliminar de contratos e documentos executado diretamente no navegador.

O **LexScan Brasil** importa documentos, extrai o texto, realiza uma triagem estrutural e linguística e apresenta alertas jurídicos por setor. O sistema foi projetado como ferramenta educacional de apoio à revisão documental. Ele **não substitui parecer jurídico, revisão profissional ou consulta às fontes oficiais vigentes**.

---

## 1. Visão geral

O projeto é distribuído em um único arquivo principal:

```text
index.html
```

Nesse arquivo estão integrados:

- estrutura HTML;
- estilos CSS;
- regras de responsividade;
- modo claro e escuro;
- importação e leitura de arquivos;
- regras de análise textual;
- alertas jurídicos;
- referências legais;
- referências jurisprudenciais para conferência;
- pontuações do relatório;
- geração do relatório HTML para download.

As bibliotecas usadas para leitura de PDF e DOCX são carregadas externamente por CDN.

---

## 2. Objetivo

O sistema ajuda a localizar pontos que merecem revisão, como:

- ausência de identificação adequada das partes;
- falta de objeto, escopo ou finalidade;
- inexistência de prazo ou vigência;
- ausência de regras de rescisão;
- falta de mecanismo para solução de controvérsias;
- termos potencialmente ambíguos;
- cláusulas com poder unilateral amplo;
- omissões jurídicas relacionadas ao setor selecionado;
- indícios que exigem conferência com legislação e jurisprudência.

O resultado deve ser interpretado como uma **triagem preliminar**. Um alerta não representa, por si só, confirmação de ilegalidade. A ausência de alerta também não representa aprovação jurídica do documento.

---

## 3. Formatos suportados

### TXT

O conteúdo é lido diretamente pelo navegador.

### PDF

O sistema usa **PDF.js** para extrair texto de PDFs que contenham texto selecionável.

Limitação: PDFs formados apenas por imagens digitalizadas podem não produzir texto. Nesse caso, é necessário acrescentar OCR ao projeto ou converter previamente o documento em PDF pesquisável.

### DOCX

O sistema usa **Mammoth.js** para converter o conteúdo do documento Word e extrair seu texto.

A conversão prioriza a informação textual. Elementos complexos de formatação podem não ser reproduzidos integralmente.

---

## 4. Como executar

1. Mantenha o arquivo com o nome `index.html`.
2. Abra o arquivo em um navegador moderno.
3. Escolha o setor do documento.
4. Importe um arquivo TXT, PDF ou DOCX, ou cole o texto manualmente.
5. Aguarde a extração do conteúdo.
6. Confira o texto no campo **Texto extraído**.
7. Selecione **Analisar documento**.
8. Revise as pontuações e os alertas.
9. Use **Baixar HTML** para gerar uma cópia do relatório.

A importação de PDF e DOCX requer conexão com a internet para carregar as bibliotecas externas.

---

## 5. Setores disponíveis

O seletor de setor oferece as seguintes categorias:

- Civil / serviços;
- Consumo;
- Trabalhista;
- Tecnologia e dados;
- Imobiliário;
- Societário;
- Contratação pública.

O setor selecionado determina quais regras jurídicas adicionais serão executadas. Se o setor for alterado depois de uma análise, o sistema refaz a análise automaticamente quando houver texto suficiente.

---

## 6. Análise estrutural geral

As verificações gerais procuram identificar elementos como:

### Partes

Procura denominações usuais, como:

- contratante;
- contratada;
- partes;
- locador;
- locatário;
- empregador;
- empregado.

Quando essas denominações não são encontradas, o relatório recomenda conferir nomes, documentos, endereços e poderes de representação.

### Objeto e escopo

Verifica a presença de referências a:

- objeto;
- escopo;
- finalidade.

### Prazo e vigência

Verifica referências a:

- prazo;
- vigência;
- duração;
- término.

### Encerramento e rescisão

Procura expressões relacionadas a:

- rescisão;
- distrato;
- encerramento.

### Solução de controvérsias

Procura referências a:

- foro;
- arbitragem;
- mediação.

---

## 7. Análise de termos ambíguos

O analisador procura expressões cadastradas como potencialmente vagas. Na versão-base analisada, estão incluídas expressões como:

- eventualmente;
- razoável;
- adequado;
- quando necessário;
- a critério.

Para cada ocorrência, o sistema pode informar:

- expressão encontrada;
- número aproximado do parágrafo;
- número aproximado da linha;
- trecho ao redor da expressão;
- sugestão automática de redação mais objetiva.

A sugestão é heurística. Ela deve ser revisada para garantir concordância gramatical, coerência jurídica e preservação do sentido original.

---

## 8. Alertas jurídicos por setor

### 8.1 Civil / serviços

O sistema procura:

- definição de obrigações;
- responsabilidade;
- indenização;
- inadimplemento;
- poderes unilaterais excessivamente amplos.

Referências indicativas usadas no código incluem disposições do Código Civil relacionadas a inadimplemento, boa-fé, função social e equilíbrio contratual.

### 8.2 Consumo

O sistema procura:

- informação clara;
- preço;
- cancelamento;
- garantia;
- perda total;
- ausência de reembolso;
- renúncia ampla de direitos;
- alteração unilateral;
- exoneração total de responsabilidade.

As referências indicativas incluem dispositivos do Código de Defesa do Consumidor sobre informação, vinculação da oferta e cláusulas abusivas.

### 8.3 Trabalhista

O sistema procura:

- jornada;
- horário;
- salário;
- remuneração;
- cargo;
- função;
- exclusividade;
- subordinação;
- cumprimento de ordens;
- horário fixo;
- pessoalidade.

A presença desses elementos não confirma vínculo empregatício. Ela indica a necessidade de revisão dos fatos e do contrato à luz da legislação trabalhista.

### 8.4 Tecnologia e dados

O sistema procura:

- finalidade;
- base legal;
- consentimento;
- legítimo interesse;
- cumprimento de obrigação;
- segurança;
- incidentes;
- vazamento;
- medidas técnicas;
- autorizações excessivamente amplas para tratamento e compartilhamento.

As referências indicativas incluem princípios, bases legais e deveres de segurança da LGPD.

### 8.5 Imobiliário

O sistema procura:

- aluguel;
- reajuste;
- garantia;
- caução;
- fiador;
- vistoria;
- multa integral ou total;
- multa sem proporcionalidade.

As referências indicativas incluem dispositivos da Lei do Inquilinato relacionados à devolução antecipada, aluguel, deveres das partes e garantias locatícias.

### 8.6 Societário

O sistema procura:

- objeto social;
- capital social;
- administrador ou administração;
- participação;
- quotas;
- ações;
- conflito de interesses;
- vantagem ou benefício particular.

As referências indicativas variam entre o Código Civil e a Lei das Sociedades por Ações, de acordo com a natureza do alerta.

### 8.7 Contratação pública

O sistema procura:

- objeto;
- vinculação;
- legislação aplicável;
- execução;
- pagamento;
- fiscalização;
- sanções;
- gestor ou fiscal do contrato.

As referências indicativas incluem artigos da Lei nº 14.133/2021 relativos às cláusulas necessárias e à fiscalização contratual.

---

## 9. Localização da cláusula relacionada

Os alertas jurídicos tentam localizar no texto a expressão que acionou a regra.

Quando encontrada, o relatório mostra:

- parágrafo aproximado;
- linha aproximada;
- trecho ao redor da ocorrência.

Quando a análise aponta uma omissão, pode aparecer a mensagem de que a cláusula relacionada não foi localizada. Isso significa que o sistema buscou determinadas palavras ou padrões, mas não os encontrou.

A numeração é aproximada porque depende das quebras de linha existentes no texto extraído. PDFs e DOCX podem perder parte da estrutura original durante a conversão.

---

## 10. Níveis de risco

Os cartões do relatório são classificados de acordo com o tipo de achado:

### Alto

Aplicado a sinais que podem exigir atenção jurídica prioritária, como possíveis limitações excessivas de direitos, omissões importantes ou cláusulas identificadas pelas regras de maior impacto.

### Médio

Aplicado a itens que merecem revisão, como ambiguidades, ausência de detalhes ou necessidade de esclarecer critérios.

### Baixo

Aplicado quando a triagem básica não detecta omissões simples dentro das regras programadas.

Os níveis são heurísticos. Eles não representam uma classificação jurídica definitiva.

---

## 11. Pontuações

O relatório apresenta três indicadores:

### Completude

Avalia a presença de elementos estruturais esperados, como partes, objeto, prazo e informações setoriais básicas.

### Redação

É reduzida quando o sistema encontra expressões potencialmente vagas.

### Atenção jurídica

É reduzida quando o sistema detecta omissões ou padrões jurídicos cadastrados como relevantes.

O **índice preliminar** é calculado a partir da média desses três indicadores.

Essas pontuações não representam probabilidade de êxito jurídico, validade contratual ou certificação de conformidade.

---

## 12. Jurisprudência para conferência

O código adiciona uma referência jurisprudencial ou uma orientação de pesquisa conforme o setor selecionado.

As referências têm caráter indicativo. O sistema não verifica automaticamente se:

- o precedente continua vigente;
- houve superação do entendimento;
- o caso analisado apresenta os mesmos fatos;
- existe súmula, tema repetitivo ou decisão posterior;
- a referência é diretamente aplicável a cada alerta específico.

Por isso, a jurisprudência deve ser conferida antes de ser usada em parecer, negociação ou processo.

---

## 13. Relatório HTML

O botão **Baixar HTML** gera um relatório contendo:

- índice preliminar;
- títulos dos alertas;
- detalhes dos achados;
- referências adicionadas ao resultado.

O arquivo é criado no navegador usando `Blob` e `URL.createObjectURL`.

O relatório baixado é uma fotografia do resultado naquele momento. Ele não mantém vínculo automático com o documento original nem recebe atualizações posteriores.

---

## 14. Privacidade e processamento local

A leitura e a análise textual são executadas no navegador.

O código do projeto não implementa envio deliberado do conteúdo do contrato para um servidor próprio. No entanto:

- PDF.js e Mammoth.js são carregados por CDN;
- abrir o projeto com internet gera solicitações para carregar essas bibliotecas;
- políticas do navegador, extensões instaladas e ambiente de rede não são controlados pelo projeto.

Para um ambiente mais restrito, as bibliotecas podem ser hospedadas localmente depois de uma revisão técnica e de licenciamento.

---

## 15. Dependências externas

O `index.html` carrega:

```text
PDF.js 3.11.174
Mammoth.js 1.12.1
```

As versões estão fixadas nas URLs do código. Antes de atualizar qualquer biblioteca:

1. faça uma cópia de segurança;
2. confira as notas de versão;
3. verifique mudanças de API;
4. teste TXT, PDF e DOCX;
5. teste o worker do PDF.js;
6. valide em navegadores desktop e móveis;
7. confira modo claro e escuro.

---

## 16. Requisitos técnicos

- navegador moderno com JavaScript habilitado;
- suporte a `FileReader` e `File.arrayBuffer()`;
- suporte a `Blob` e `URL.createObjectURL()`;
- conexão com a internet para carregar PDF.js e Mammoth.js;
- PDF com texto selecionável para extração sem OCR.

---

## 17. Compatibilidade visual

O layout possui:

- design responsivo;
- grade em duas colunas em telas maiores;
- coluna única em telas menores;
- modo claro;
- modo escuro baseado em `prefers-color-scheme`;
- correções específicas de contraste para:
  - texto importado;
  - seletor de setor;
  - seletor de arquivo;
  - opções do seletor;
  - botão de escolha de arquivo.

---

## 18. Limitações conhecidas

O sistema não realiza:

- parecer jurídico completo;
- validação oficial de conformidade;
- consulta jurídica em tempo real;
- atualização automática da legislação;
- atualização automática da jurisprudência;
- análise semântica profunda de todo o contrato;
- comparação entre todas as cláusulas;
- detecção garantida de contradições internas;
- consulta de leis estaduais ou municipais;
- identificação automática de todas as normas regulatórias;
- OCR de PDFs digitalizados;
- validação de assinatura digital;
- análise de anexos não importados;
- confirmação de que uma cláusula é legal ou ilegal.

As regras são baseadas em palavras-chave, expressões regulares e condições programadas.

---

## 19. Possíveis falsos positivos

Uma expressão pode ser sinalizada mesmo quando seu uso é juridicamente correto no contexto.

Exemplos:

- “força maior”;
- “caso fortuito”;
- “razoável”;
- “material”;
- “imediatamente”.

O relatório deve explicar que a expressão merece precisão, não que esteja necessariamente errada.

---

## 20. Possíveis falsos negativos

O sistema pode deixar de emitir alerta quando:

- a mesma ideia é redigida com palavras não cadastradas;
- a irregularidade depende de fatos externos;
- a regra depende de legislação local;
- duas cláusulas se contradizem sem usar palavras-chave previstas;
- a cláusula exige interpretação jurídica especializada;
- o documento extraído perdeu estrutura ou conteúdo.

---

## 21. Manutenção recomendada

A base deve ser revisada periodicamente para atualizar:

- legislação;
- numeração de artigos;
- regulamentações;
- jurisprudência;
- súmulas e temas repetitivos;
- regras por setor;
- expressões vagas;
- sugestões de redação;
- bibliotecas PDF.js e Mammoth.js;
- compatibilidade com navegadores;
- segurança das dependências.

Toda atualização deve ser feita sobre a versão mais recente do `index.html`, preservando uma cópia de segurança.

---

## 22. Procedimento seguro para alterações

1. Duplique o arquivo atual.
2. Nomeie a cópia de segurança com data ou versão.
3. Faça apenas a alteração solicitada.
4. Não remova regras existentes sem revisão.
5. Valide a sintaxe do JavaScript.
6. Teste o carregamento da página.
7. Teste a importação dos três formatos.
8. Teste todos os setores.
9. Teste o relatório baixado.
10. Compare visualmente com a versão anterior.

---

## 23. Estrutura lógica simplificada

```text
Inicialização
├── configura PDF.js
├── registra eventos dos campos
└── prepara estado do relatório

Importação
├── TXT → leitura direta
├── PDF → PDF.js → texto por página
└── DOCX → Mammoth.js → HTML → texto

Análise
├── normaliza texto
├── verifica estrutura geral
├── procura expressões vagas
├── aplica regras do setor
├── localiza trechos
├── calcula pontuações
└── monta alertas

Pós-processamento
├── adiciona nível de risco
├── adiciona setor
├── adiciona jurisprudência indicativa
└── atualiza ao trocar o setor

Exportação
└── gera relatório HTML para download
```

---

## 24. Aviso jurídico

O LexScan Brasil é um protótipo educacional de triagem documental.

Ele não substitui:

- advogado;
- contador;
- profissional de compliance;
- encarregado de proteção de dados;
- especialista regulatório;
- análise de fatos e documentos complementares;
- consulta às fontes oficiais vigentes.

Use os resultados para organizar a revisão e levantar perguntas. Não tome decisões jurídicas relevantes exclusivamente com base na pontuação ou nos alertas automáticos.

---

## 25. Licenciamento

O projeto ainda não declara uma licença própria no arquivo principal. Antes de distribuir, comercializar ou publicar, defina uma licença para o código e confira separadamente as licenças das dependências externas.

---

## 26. Versão documentada

Este README descreve a versão do `index.html` disponibilizada nesta etapa da conversa, incluindo:

- layout profissional;
- importação TXT/PDF/DOCX;
- análise estrutural;
- alertas jurídicos setoriais;
- localização de trechos;
- sugestões de redação;
- níveis de risco;
- jurisprudência indicativa;
- atualização automática ao trocar o setor;
- exportação de relatório HTML.

Your site is live at https://alcane1959.github.io/lexscan-brasil/
