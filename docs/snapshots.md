Funcionalidade: **Visualização de Snapshots**

Essa funcionalidade permite ver o histórico completo de versões da tabela Iceberg. Cada snapshot representa um estado da tabela após uma operação, como inserção de dados, compactação ou deleção.

A interface deve mostrar uma lista de snapshots com as principais informações de cada um. Isso permite entender quando a tabela foi modificada, qual operação ocorreu e qual foi o impacto dessa mudança.

---

Funcionalidade: **Lista de Snapshots**

A página da tabela deve ter uma seção chamada *Snapshots*. Nela aparece uma tabela com o histórico das versões da tabela.

Informações exibidas para cada snapshot:

1. **Snapshot ID** — identificador único do snapshot
2. **Timestamp** — momento em que o snapshot foi criado
3. **Operation** — tipo de operação que gerou o snapshot
4. **Parent Snapshot** — snapshot anterior na linha do tempo
5. **Summary** — resumo da operação
6. **Manifest Count** — quantidade de manifests associados
7. **Data Files Added** — arquivos adicionados
8. **Data Files Removed** — arquivos removidos

Isso permite entender rapidamente o que mudou na tabela ao longo do tempo.

---

Funcionalidade: **Tipos de Operação**

Cada snapshot possui um campo indicando qual operação gerou aquela versão da tabela. Os principais tipos que devem aparecer são:

1. **append** — novos dados foram adicionados
2. **overwrite** — dados foram reescritos ou substituídos
3. **delete** — dados foram removidos
4. **replace** — arquivos foram substituídos (normal em compactação)
5. **rewrite** — reescrita de arquivos para reorganização
6. **fast append** — inserção otimizada de arquivos

Mostrar esse tipo de operação ajuda a entender o comportamento da pipeline que escreve na tabela.

---

Funcionalidade: **Linha do Tempo da Tabela**

Além da lista, pode existir uma visualização cronológica simples mostrando quando as operações aconteceram.

Exemplo conceitual:

10:00 — append
12:30 — append
14:10 — append
18:00 — rewrite (compactação)
23:00 — expire snapshots

Isso ajuda a visualizar o padrão de atualizações da tabela.

---

Funcionalidade: **Detalhes do Snapshot**

Ao clicar em um snapshot, a interface pode mostrar detalhes adicionais daquela versão.

Informações úteis:

1. Quantidade total de arquivos naquele snapshot
2. Tamanho total da tabela naquele momento
3. Manifests associados
4. Partições afetadas
5. Arquivos adicionados ou removidos
6. Estatísticas de dados alterados

Isso ajuda a entender exatamente o impacto daquela operação.

---

Funcionalidade: **Comparação entre Snapshots**

A interface pode permitir selecionar dois snapshots para ver a diferença entre eles.

Informações exibidas:

1. Arquivos adicionados
2. Arquivos removidos
3. Mudança no tamanho total da tabela
4. Partições modificadas

Isso facilita investigar mudanças inesperadas na tabela.

---

Funcionalidade: **Expiração de Snapshots**

A interface também pode permitir gerenciar retenção de snapshots.

Configurações possíveis:

1. Manter snapshots por número mínimo (ex: manter últimos 10)
2. Manter snapshots por tempo (ex: manter últimos 7 dias)
3. Executar limpeza manual
4. Agendar expiração periódica

Essa funcionalidade evita crescimento excessivo dos metadados.

---

Funcionalidade: **Indicadores de Snapshot**

A página pode mostrar alguns indicadores importantes:

1. Quantidade total de snapshots
2. Snapshot mais antigo
3. Snapshot atual da tabela
4. Crescimento recente de snapshots

Essas informações ajudam a entender se a retenção está adequada.

---

Funcionalidade: Grafo de Snapshots

A página de snapshots deve mostrar um grafo que representa a evolução da tabela ao longo do tempo. Cada nó representa um snapshot e cada conexão representa a relação com o snapshot anterior. Isso permite visualizar como a tabela evoluiu após cada operação.

Cada nó do grafo deve mostrar informações básicas como o momento em que o snapshot foi criado e o tipo de operação que o gerou. O snapshot atual da tabela deve aparecer destacado para indicar qual versão está ativa.

Os snapshots devem ser identificados pelo tipo de operação que os gerou, como inserção de dados, sobrescrita, deleção ou reescrita de arquivos. Isso ajuda a entender rapidamente o comportamento da tabela ao longo do tempo, como momentos de ingestão de dados ou execuções de compactação.

O grafo deve permitir interação. Ao clicar em um snapshot, o usuário pode abrir um painel com detalhes daquela versão da tabela, incluindo horário da operação, tipo de operação, quantidade de arquivos adicionados ou removidos e outras informações relevantes.

Para tabelas com muitos snapshots, a visualização pode permitir limitar o número de snapshots exibidos, por exemplo mostrando apenas os mais recentes ou apenas snapshots dentro de um intervalo de tempo. Isso evita que o grafo fique muito grande e difícil de visualizar.

As funcionalidades relacionadas a branches e tags da tabela devem ficar em uma seção separada, permitindo gerenciar ramificações sem misturar com a linha principal de snapshots.

Essas funcionalidades cobrem praticamente tudo que está na **tabela de snapshots do Iceberg**, permitindo explorar histórico, entender operações e controlar retenção.

