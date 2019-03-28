# INE5645-05238A (20191) - Programação Paralela e Distribuída  
Rodrigo Chaves - 15205303

### Tarefa 1:

1. Que função da biblioteca do OpenMP é utilizada?  
   R: omp_get_thread_num() e omp_get_num_threads()

2. As threads no #pragma paralell são todas diferentes. (verdadeiro/falso)  
   R: Verdadeiro

================================

### Tarefa 2:
O que ocorre no programa, com relação ao loop for dentro do ##pragma paralell ?

R: Executa o laço de repetição `for` de forma paralela, em 8 threads configuradas em `#define THREADS 8`,
   realizando 100 repetições (executadas paralelamente em 8 threads) definido em `#define N 100`.
   O laço identifica o numero da thread e o numero de iteração do loop.

===============================

### Tarefa 3:
O que esta ocorrendo no programa ?

R: O OpenMP atribui um conjunto de iteração sequencial para cada thread. De forma que (N/THREADS) loops serão alocadas de forma sequencial nas threads.

Thread 0 = {0, 1, 2, 3}
Thread 1 = {4, 5, 6, 7}
[...]
Thread n = {x, x+1, x+2, x+3}

===============================

### Tarefa 4: 

1. O que caracteriza o programa acima, em relação programa da Tarefa 3?
R: Na tarefa 3 é utilizado: `schedule(static)`, e nesta tarefa é utilizado `schedule(dynamic)`.

2. Por que este programa é mais rápido do que o da Tarefa 3?
R: Porque vai alocar o processo na primeira thread que estiver liberada para executar. Assim o processamento cai de 54seg para 36seg. Na tarefa 3 ele já enfileirava os processos divididos nas threads antes de saber se estava liberada. 

3. Para que serve dynamic schedules?
R: Dynamic scheduled é melhor quando as iterações podem tomar quantidades de tempo DIFERENTES. Após cada iteração, as threads devem parar e receber um novo valor da variável `i` do loop, a ser usada em sua próxima iteração (repetição).

===============================

### Tarefa 5: 
O que você pode concluir, comparando estes dois programas ? Qual executará mais rapido?  Por que?

Executará mais rapido no segundo exemplo, porque as threads tem tempos de execução estático (igual para todas as threads).
