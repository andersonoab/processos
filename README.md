# Leitor de Processos Trabalhistas — Sonova

## Abrir

1. Extraia o ZIP inteiro, mantendo `index.html` e a pasta `vendor` no mesmo diretório.
2. Abra `index.html` com duplo clique no Chrome ou Edge.
3. Clique em **Ler Excel** e selecione os relatórios.

As bibliotecas de Excel e gráficos estão incluídas, nas mesmas versões do projeto original. A análise funciona sem servidor e sem conexão; as fontes Google são opcionais e usam uma fonte substituta quando indisponíveis.

## Leitura principal

- **Primeira faixa: Valor da causa.** Usa somente o campo Valor da Causa, com o total completo e centavos. Se esse campo estiver ausente, o risco econômico não o substitui. O painel indica quantos processos estão sem valor informado.
- **Segunda faixa: Valor provável.** Usa somente a coluna Risco Econômico — Provável. Possível acima de 50% não integra a base de provisão.
- Os valores da causa e provável são medidas distintas e não são somados entre si.
- Os outros indicadores de risco e garantias estão na seção expansível abaixo das faixas.
- Os indicadores acompanham os filtros da lateral e dos cards. Um clique filtra; outro remove o filtro. O duplo clique abre a composição.

## Gráficos em valor da causa

Todos os gráficos monetários utilizam somente a coluna **Valor da Causa**: ranking por processo, prognóstico, empresa, fase e pedidos. Os gráficos de quantidade e prazo preservam suas unidades. A faixa separada de provável no resumo permanece disponível.

O ranking é ordenado pelo valor da causa. Valores de risco econômico não determinam barras, eixos, totais ou ordem. Um processo com risco zero e causa informada continua no ranking.

A classificação por prognóstico utiliza o valor da causa de cada processo uma única vez. Isso não transforma valor da causa em provisão. O comparativo contra risco econômico foi substituído por valor da causa por fase.

A distribuição por pedido é um **rateio gerencial igual entre as categorias identificadas**, com ajuste do resíduo no último item para fechar com a causa. Não usa valores de risco como pesos e não representa valores individuais da petição. A descrição do gráfico e o detalhe informam essa regra.

A evolução mensal só apresenta valores da causa explícitos por competência. Quando a fonte não contém esse histórico, o gráfico informa a ausência. O histórico original de contingência foi preservado nas tabelas, sem ser utilizado como valor da causa.

## Arquivados

O leitor percorre também as abas Arquivados/Encerrados. Processos com status explícito de encerramento ou data válida de arquivamento também são tratados como arquivados. Risco zero, sozinho, não muda a situação do processo.

Os arquivados continuam na carteira, na pesquisa, nas fichas e na exportação. Use **Situação → Arquivado** para consultá-los. Seu prognóstico interno aparece como **ARQUIVADO / SEM RISCO**, preservando o prognóstico original na ficha e na exportação.

Os valores originais das linhas arquivadas são históricos e não entram nos totais financeiros de causa, risco e provisão, na exposição por pedido, nos gráficos financeiros ou na evolução consolidada. Garantias permanecem separadas, como capital em juízo, inclusive quando houver garantia histórica de processo arquivado.

A exportação mantém os dados originais e acrescenta **Compõe totais financeiros**, **Valor da causa no controle**, **Valor provável no controle**, **Base de provisão (somente provável)** e **Prognóstico original**. Assim, os totais do controle podem ser reconciliados sem apagar o histórico.

## Reconhecimento das planilhas

Cabeçalhos genéricos como `Valor` e `Número`, sem contexto jurídico, não são interpretados como Valor da Causa e Número do Processo. Isso evita que demonstrativos auxiliares sejam adicionados à carteira. A metodologia apresenta as abas reconhecidas e ignoradas.

Os valores são lidos das células numéricas, conservando sua precisão original até a apresentação. A apresentação arredonda para duas casas decimais.

## Validação desta alteração

O relatório fornecido de 09/10/2026 foi usado na validação, sem ser incorporado ao HTML ou ao ZIP:

| Indicador | Resultado |
| --- | ---: |
| Processos não arquivados | 9 |
| Valor da causa sem arquivados | R$ 1.854.454,89 |
| Valor provável sem arquivados | R$ 684.135,78 |
| Processos arquivados para consulta | 16 |

Foram conferidos leitura da base real, exclusão das abas auxiliares, filtros, consulta dos arquivados, preservação das fichas, ordenação, composição dos gráficos pelo valor da causa, exportação filtrada e cenário de histórico mensal com valores em Provável e Possível acima de 50%.

Os dados carregados ficam somente na memória da página. Fechar, recarregar ou resetar elimina os dados da sessão; os arquivos Excel originais não são alterados.

## Dependências

- SheetJS / XLSX 0.18.5 (Apache-2.0).
- Chart.js 4.4.1 (MIT).
- chartjs-plugin-datalabels 2.2.0 (MIT).

Os avisos de licença das dependências permanecem nos arquivos distribuídos. A licença original do projeto permanece em `LICENSE`.
