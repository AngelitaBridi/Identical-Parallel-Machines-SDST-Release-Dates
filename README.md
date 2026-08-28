# Programação em Máquinas Paralelas Idênticas com Setup Dependente da Sequência: Cenários com e sem Datas de Liberação

Este repositório contém os códigos, instâncias e resultados computacionais utilizados no estudo do problema de programação em máquinas paralelas idênticas com tempos de setup dependentes da sequência, considerando cenários com e sem datas de liberação das tarefas.

O objetivo considerado nos experimentos computacionais é a minimização do makespan, correspondente ao instante de conclusão da última tarefa do conjunto programado.

São considerados três cenários experimentais:

1. Sem datas de liberação
2. Datas de liberação folgadas
3. Datas de liberação justas

Para cada cenário são avaliadas instâncias estruturadas e não estruturadas.

## Métodos computacionais

Os experimentos comparam duas abordagens de solução:

- Heurística 3-Fases
- Hexaly Optimizer

### Heurística 3-Fases

A Heurística 3-Fases utilizada neste estudo foi proposta por Paulo M. França, Michel Gendreau, Gilbert Laporte e Felipe M. Müller, em 1996, para o problema de programação em máquinas paralelas idênticas com tempos de setup dependentes da sequência e minimização do makespan.
O método é composto por três fases:
1. construção de uma solução inicial;
2. melhoria da solução por meio de busca tabu;
3. refinamento adicional da solução obtida.
Para os cenários com datas de liberação, a Heurística 3-Fases foi adaptada para considerar o instante a partir do qual cada tarefa se encontra disponível para processamento.

### Hexaly Optimizer

O Hexaly Optimizer é utilizado para resolver as mesmas instâncias consideradas pela Heurística 3-Fases.
O modelo realiza a alocação e o sequenciamento das tarefas nas máquinas, considerando os tempos de processamento, os tempos de setup dependentes da sequência e, nos cenários correspondentes, as datas de liberação das tarefas.
O objetivo do modelo é minimizar o makespan.

## Instâncias

As instâncias são caracterizadas pelo número de máquinas, número de tarefas, tempos de processamento e matriz de tempos de setup dependentes da sequência.
Foram consideradas as seguintes dimensões:
- 2, 3, 4 e 5 máquinas
- 20, 30, 40 e 50 tarefas
- 10 instâncias para cada combinação entre número de máquinas e número de tarefas

As instâncias são divididas em dois grupos.

### Instâncias estruturadas

Nas instâncias estruturadas, os tempos de setup são obtidos a partir de distâncias euclidianas truncadas entre pontos gerados aleatoriamente, produzindo uma matriz assimétrica de tempos de setup que satisfaz a desigualdade triangular.

### Instâncias não estruturadas

Nas instâncias não estruturadas, os tempos de processamento e os tempos de setup dependentes da sequência são gerados aleatoriamente como valores inteiros no intervalo de 1 a 99.
Para cada cenário são consideradas 320 instâncias, sendo 160 estruturadas e 160 não estruturadas.

## Cenários experimentais

### Sem datas de liberação

Neste cenário, todas as tarefas estão disponíveis desde o início do horizonte de programação.
O sequenciamento depende da alocação das tarefas entre as máquinas, dos tempos de processamento e dos tempos de setup dependentes da sequência.

### Datas de liberação folgadas

Neste cenário, cada tarefa possui uma data de liberação que determina o instante a partir do qual seu processamento pode ser iniciado.
As datas de liberação são menos restritivas, proporcionando maior flexibilidade para o sequenciamento das tarefas.

### Datas de liberação justas

Neste cenário, as datas de liberação impõem uma restrição temporal mais significativa.
A menor disponibilidade temporal das tarefas pode provocar períodos de ociosidade das máquinas e reduzir as possibilidades de reorganização das sequências.

## Estrutura do repositório

O repositório está organizado em duas pastas principais:

### Heuristica_3_Fases

Contém os códigos, geradores de instâncias, instâncias utilizadas e resultados obtidos com a Heurística 3-Fases.
Os experimentos estão organizados em:
- 01_Sem_Release
- 02_Com_Release_Folgado
- 03_Com_Release_Justo

### Hexaly

Contém os códigos utilizados no Hexaly Optimizer, as instâncias e os resultados computacionais obtidos pelo solver.
Os experimentos estão organizados em:
- 01_Sem_Release_Hexaly
- 02_Release_Folgado_Hexaly
- 03_Release_Justo_Hexaly

Em cada cenário, as instâncias e os resultados são separados entre casos estruturados e não estruturados.

## Comparação computacional

As mesmas instâncias são utilizadas na Heurística 3-Fases e no Hexaly Optimizer, permitindo a comparação direta entre os métodos.

A estrutura experimental permite analisar o comportamento das soluções em função:
- do número de tarefas;
- do número de máquinas;
- da estrutura dos tempos de setup;
- da presença ou ausência de datas de liberação;
- do grau de restrição imposto pelas datas de liberação.

Os arquivos disponibilizados neste repositório permitem identificar os códigos utilizados, as instâncias avaliadas e os respectivos resultados computacionais.

## Referência da Heurística 3-Fases

França, P. M.; Gendreau, M.; Laporte, G.; Müller, F. M. A tabu search heuristic for the multiprocessor scheduling problem with sequence dependent setup times. International Journal of Production Economics, v. 43, n. 2–3, p. 79–89, 1996. DOI: https://doi.org/10.1016/0925-5273(96)00031-X
