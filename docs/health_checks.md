Check 1: **Small Files**
Ele verifica se a tabela possui arquivos muito pequenos, o que pode degradar a performance de leitura.

1. **Saudável** quando tamanho médio dos arquivos ≥ 128MB
2. **Warning** quando tamanho médio dos arquivos ≥ 64MB e < 128MB
3. **Crítico** quando tamanho médio dos arquivos < 64MB

---

Check 2: **Snapshots**
Ele verifica se a tabela acumulou muitos snapshots, o que aumenta o tamanho dos metadados e o tempo de planejamento das queries.

1. **Saudável** quando snapshots < 50
2. **Warning** quando snapshots ≥ 50 e < 200
3. **Crítico** quando snapshots ≥ 200

---

Check 3: **Manifests**
Ele verifica se a quantidade de manifests está alta, o que pode aumentar o tempo de planejamento das consultas.

1. **Saudável** quando manifests < 100
2. **Warning** quando manifests ≥ 100 e < 500
3. **Crítico** quando manifests ≥ 500

---

Check 4: **Delete Files**
Ele verifica se existem muitos arquivos de delete em relação aos arquivos de dados, o que pode degradar a performance de leitura.

1. **Saudável** quando delete files < 10% dos data files
2. **Warning** quando delete files ≥ 10% e < 30% dos data files
3. **Crítico** quando delete files ≥ 30% dos data files

---

Check 5: **Metadata Size**
Ele verifica se os arquivos de metadados da tabela estão crescendo demais.

1. **Saudável** quando metadata < 50MB
2. **Warning** quando metadata ≥ 50MB e < 200MB
3. **Crítico** quando metadata ≥ 200MB

---

Check 6: **Orphan Files**
Ele verifica se existem arquivos no storage que não pertencem a nenhum snapshot da tabela.

1. **Saudável** quando não existem orphan files
2. **Warning** quando orphan files ≥ 1GB
3. **Crítico** quando orphan files ≥ 100GB

---

Funcionalidade: **Configuração de Health Checks**
Permite definir os limites e regras utilizados para avaliar a saúde das tabelas. Como diferentes empresas possuem volumes de dados e padrões operacionais distintos, os thresholds dos checks não devem ser fixos. Essa seção permite ajustar os valores que determinam quando um check está saudável, em alerta ou crítico.

Cada health check pode ter seus próprios parâmetros configuráveis. Por exemplo, no check de small files é possível definir qual tamanho médio de arquivo é considerado saudável, qual faixa representa alerta e qual caracteriza uma situação crítica. O mesmo pode ser configurado para número de snapshots, quantidade de manifests, proporção de delete files ou volume de orphan files.

As configurações podem ser aplicadas em diferentes níveis. Elas podem ser globais para todo o sistema, aplicadas a um catálogo ou schema específico, ou definidas individualmente para uma tabela. Isso permite que diferentes tipos de dados tenham regras de monitoramento diferentes.

A interface também deve mostrar os valores atualmente configurados para cada check, permitindo que sejam alterados facilmente quando necessário.

Níveis de avaliação:

1. **Saudável** quando a métrica da tabela está dentro do limite considerado seguro
2. **Warning** quando a métrica ultrapassa o limite de alerta configurado e pode indicar um problema em crescimento
3. **Crítico** quando a métrica ultrapassa o limite crítico e indica que uma ação de manutenção deve ser executada

Essa funcionalidade garante que os health checks se adaptem ao contexto operacional de cada organização, evitando alertas desnecessários ou regras rígidas que não refletem a realidade do ambiente de dados.

