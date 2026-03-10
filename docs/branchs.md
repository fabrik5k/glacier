Funcionalidade: **Visão Geral de Branches**

A seção de branches mostra todas as branches existentes da tabela Iceberg. A interface deve indicar quantas branches existem, qual é a branch principal e qual snapshot cada branch está referenciando. Isso permite entender rapidamente quantas linhas de evolução da tabela existem.

---

Funcionalidade: **Lista de Branches**

Deve existir uma lista simples mostrando todas as branches da tabela.

Informações exibidas:

1. Nome da branch
2. Snapshot atual da branch
3. Data da última atualização
4. Origem da branch (de qual snapshot foi criada)

Isso permite ver rapidamente qual branch está ativa e quais estão paradas.

---

Funcionalidade: **Grafo de Branches**

A interface deve mostrar um grafo inspirado em ferramentas como GitKraken, onde é possível visualizar o lineage das branches. Cada linha representa uma branch e os pontos representam snapshots.

Esse grafo permite visualizar:

1. Onde uma branch foi criada
2. Como as branches divergem da linha principal
3. Em qual snapshot cada branch está posicionada

Isso ajuda a entender a evolução paralela da tabela.

---

Funcionalidade: **Snapshot Atual da Branch**

Cada branch deve mostrar claramente qual snapshot está sendo usado naquele momento. Isso indica qual versão da tabela aquela branch está enxergando.

---

Funcionalidade: **Detalhes da Branch**

Ao selecionar uma branch, a interface pode mostrar informações adicionais:

1. Snapshot atual da branch
2. Snapshot de origem da branch
3. Histórico de snapshots dentro da branch
4. Data da última atualização

---

Funcionalidade: **Criação de Branch**

A interface deve permitir criar uma nova branch a partir de um snapshot específico da tabela. Isso permite criar linhas paralelas para experimentação ou processamento isolado.

---

Funcionalidade: **Gerenciamento de Branch**

A seção também deve permitir operações básicas sobre branches:

1. Criar nova branch
2. Atualizar a branch para um novo snapshot
3. Remover uma branch
4. Navegar para o snapshot que a branch está apontando

Essas funcionalidades permitem controlar diferentes versões da tabela sem interferir na linha principal de snapshots.

