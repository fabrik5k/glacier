Funcionalidade: **Informações da Tabela**

Essa seção mostra os principais metadados e indicadores da tabela Iceberg. O objetivo é permitir que o usuário entenda rapidamente a estrutura da tabela, seu tamanho e seu estado atual.

Informações exibidas:

1. Nome da tabela
2. Catálogo e schema
3. Location no storage
4. Tamanho total da tabela
5. Quantidade de arquivos de dados
6. Tamanho médio dos arquivos
7. Quantidade de snapshots
8. Snapshot atual (HEAD)

Também podem aparecer alguns indicadores adicionais úteis:

9. Quantidade de manifests
10. Quantidade de delete files
11. Quantidade de orphan files detectados

---

Funcionalidade: **Estrutura da Tabela**

Dentro dessa mesma seção também pode aparecer a estrutura da tabela.

Informações exibidas:

1. Schema da tabela (colunas e tipos)
2. Partition spec
3. Sort order
4. Bucketing

Isso ajuda a entender como os dados estão organizados fisicamente.

---

Funcionalidade: **Estatísticas da Tabela**

Uma parte visual pode mostrar estatísticas importantes para operação:

1. Distribuição de tamanho dos arquivos
1. Distribuição de tamanho dos arquivos por partição
2. Número total de arquivos
3. Crescimento da tabela ao longo do tempo

Essas informações ajudam a identificar problemas de fragmentação ou crescimento inesperado.
