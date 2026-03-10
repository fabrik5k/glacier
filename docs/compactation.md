Funcionalidade: **Compactação Periódica**

Ela permite configurar tarefas automáticas que reorganizam os arquivos da tabela Iceberg para melhorar performance e reduzir fragmentação. O usuário define uma política de compactação e o sistema executa essa operação periodicamente.

A interface deve permitir escolher **qual estratégia de compactação será usada**. As duas principais são **binpack** e **order**.

---

Funcionalidade: **Compactação Binpack**

Essa compactação junta vários arquivos pequenos em arquivos maiores sem alterar a ordem dos dados. O objetivo é reduzir a quantidade de arquivos e aumentar o tamanho médio deles.

Configuração da política:

1. Tabela alvo
2. Frequência de execução (diária, semanal, mensal ou cron)
3. Tamanho alvo dos arquivos (ex: 128MB, 256MB, 512MB)
4. Número mínimo de arquivos pequenos para ativar a compactação
5. Filtro opcional de partição ou intervalo de data

Essa compactação é indicada quando o problema da tabela é apenas **fragmentação de arquivos**.

---

Funcionalidade: **Compactação Order**

Essa compactação reescreve os arquivos organizando os dados por uma coluna ou conjunto de colunas. Isso melhora a leitura quando consultas filtram frequentemente por esses campos.

Configuração da política:

1. Tabela alvo
2. Colunas de ordenação
3. Frequência de execução
4. Tamanho alvo dos arquivos
5. Partições que devem ser reorganizadas

Essa estratégia é usada quando se quer **melhorar o layout físico dos dados**, não apenas reduzir small files.

---

Funcionalidade: **Compactação por Partição**

Permite compactar apenas partições específicas da tabela.

Configuração:

1. Escolher partição (ex: data)
2. Intervalo de valores (ex: últimos 7 dias)
3. Estratégia de compactação (binpack ou order)
4. Frequência da execução

Isso evita reescrever a tabela inteira.

---

Funcionalidade: **Compactação Condicional**

Permite executar a compactação apenas quando algum health check indicar problema.

Exemplos de condições:

1. Executar compactação se small files estiver em Warning ou Crítico
2. Executar compactação se número de arquivos ultrapassar um limite
3. Executar compactação apenas se tamanho médio de arquivo estiver abaixo do limite definido

Assim o sistema evita executar manutenção desnecessária.

---

Funcionalidade: **Histórico de Compactações**

A interface deve mostrar as compactações que já foram executadas.

Informações exibidas:

1. Data da execução
2. Tabela afetada
3. Estratégia utilizada (binpack ou order)
4. Quantidade de arquivos antes e depois
5. Tamanho médio antes e depois
6. Duração da operação
7. Status da execução

Isso permite acompanhar o impacto das manutenções.

---

Funcionalidade: **Simulação de Compactação**

Antes de executar a compactação o sistema pode estimar o impacto da operação.

Informações exibidas:

1. Quantidade de arquivos que serão reescritos
2. Quantidade estimada de arquivos finais
3. Tamanho médio esperado
4. Volume de dados que será reprocessado

Isso ajuda o usuário a decidir se a compactação vale a pena.
