# Cotações do Ibovespa

A análise usa a série **diária** do índice Ibovespa exportada do Investing.com, com 2.729 registros entre **02/01/2015 e 30/12/2025**. O provedor condiciona a redistribuição das cotações à autorização por escrito. O CSV é um insumo local. [Histórico do Ibovespa e condições de uso](https://br.investing.com/indices/bovespa-historical-data).

1. Use uma cópia autorizada do histórico com frequência diária e o período indicado.
2. Salve o arquivo como `data/ibovespa.csv`. Na entrega acadêmica ele se chamava `Dados Históricos - Ibovespa.csv`.
3. Mantenha a codificação UTF-8, o separador de campos vírgula e os cabeçalhos em português. O notebook usa `Data` no formato `DD.MM.AAAA`, `Abertura` e `Último`.

O arquivo original representa as cotações com ponto como separador de milhar. A leitura da entrega interpreta esses valores em **milhares de pontos**. Para reproduzir os níveis de erro absoluto e o cenário, mantenha essa convenção. O MAPE é expresso em porcentagem.
