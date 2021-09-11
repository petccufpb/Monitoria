# Teste de Aptidão - Linguagem C

## Introdução

O NumPy é uma das principais ferramentas para ciência de dados e base de
diversas bibliotecas para linguagem Python. Um dos principais motivos para sua
eficiência é que o NumPy possui diversas partes implementadas em C. O objetivo
desse projeto é criar uma implementação para representação e manipulação de
matrizes inspirada no NumPy.

## Representação da matriz

Um dos pontos fundamentais para implementação desse projeto é a forma de
representação de uma matriz. No projeto, a matriz deve ser representada por
uma struct:

```
struct matrix {
  int *data;
  int n_rows;
  int n_cols;
  int stride_rows;
  int stride_cols;
};
```

- ***data** é um array unidimensional com os dados da matriz.

Dessa forma, uma matriz do tipo:  
```
{{1, 2, 3},
{4, 5, 6},
{7, 8, 9}}
```
Será guardada como:  
```
{1, 2, 3, 4, 5, 6, 7, 8, 9}
```
Nesse sentido, todos os dados deverão ser armazenados em um array unidimensional. Portanto, os outros campos da struct serão responsáveis por determinar como a matriz deverá ser interpretada em relação às suas dimensões. Essa representação permite aumentar a eficiência de operações aplicadas sobre a matriz. 

- **n_rows** é o número de linhas da matriz.

- **n_cols** é o número de colunas da matriz.

- **stride_rows** é um número que determina quantos elementos devem ser "pulados" no array unidimensional para acessar uma próxima linha.
No exemplo acima, considerando o elemento 1 (elemento da primeira linha e da primeira coluna), se quisermos acessar a próxima linha (elemento 4), temos
que andar 3 elementos no array unidimensional. Assim, **stride_rows** tem o valor 3.

- **stride_cols** é o número que determina quantos elementos devem ser "pulados" no array unidimensional para acessar a próxima coluna.
Com uma matriz criada, **stride_cols** vai ser igual a 1, pois para acessar um elemento de uma próxima coluna basta acessar o próximo índice.
Algumas funções vão modificar esse número, então é importante defini-lo mesmo que seu valor inicial seja sempre 1.

## Funções para criação de matrizes

As funções para criação de matrizes que precisam ser implementadas são as seguintes:

### create_matrix
`struct matrix create_matrix(int *data, int n_rows, int n_cols);`  
create_matrix é a principal função para criar uma matriz.
- ***data** é um array unidimensional com os dados
- **n_rows** é o número de linhas da matriz
- **n_cols** é o número de colunas da matriz

Note que os membros **stride_rows** e **stride_cols** da struct retornada precisam ser iniciados.

### i_matrix
`struct matrix i_matrix(int n);`  
i_matrix cria uma matriz identidade.
- **n** é o tamanho da matriz. 

Lembre-se que a matriz identidade tem o mesmo número de linhas e colunas.

## Funções para acessar elementos

Essas funções deverão estabelecer uma lógica de acesso padrão aos elementos da matriz a partir dos campos da struct. Portanto, após implementadas deverão ser usadas no desenvolvimento das demais funções solicitadas. Dessa forma, as funções para acessar os elementos de uma matriz que precisam ser implementadas são as seguintes:

### get_element
`int get_element(struct matrix a_matrix, int ri, int ci);`  
get_element retorna um elemento da matriz de acordo com sua posição.  
- **a_matrix** é a matriz que vai ser acessada  
- **ri** é o índice da linha do elemento  
- **ci** é o índice da coluna do elemento

### put_element
`void put_element(struct matrix a_matrix, int ri, int ci, int elem);`  
put_element coloca um elemento na matriz de acordo com a posição.
- **a_matrix** é a matriz que vai ser acessada  
- **ri** é o índice da linha do elemento  
- **ci** é o índice da coluna do elemento 
- **elem** é o elemento que vai ser colocado

### print_matrix 
`void print_matrix(struct matrix a_matrix);`  
print_matrix exibe os dados no formato da matriz.
- **a_matrix** é a matriz que vai ser exibida

## Funções para manipulação de dimensões

Para implementar essas funções os campos da struct: **n_rows**, **n_cols**, **stride_rows** e **stride_cols** são fundamentais. 
Dessa forma, implemente as funções a seguir apenas alterando o valor dos membros da struct. 
**Sob hipótese alguma, o conteúdo do array data deverá ser alterado.** Essa implementação garante que essas funções executem com grande velocidade. 
As funções para manipulação de dimensões de matrizes que precisam ser implementadas são as seguintes:

### transpose
`struct matrix transpose(struct matrix a_matrix)`  
transpose retorna a matriz transposta.
- **a_matrix** é a matriz usada para gerar a matriz transposta

### flatten
`struct matrix flatten(struct matrix a_matrix);`  
flatten redimensiona a matriz para que todos os dados fiquem em apenas 1 linha.
- **a_matrix** é a matriz que será transformada

## Funções de agregação

As funções de agregação que precisam ser implementadas são as seguintes:

### sum
`int sum(struct matrix a_matrix);`  
sum soma todos os elementos da matriz e retorna o resultado.
- **a_matrix** é a matriz que terá seus elementos somados

### mean
`int mean(struct matrix a_matrix);`  
mean calcula a média dos elementos da matriz.
- **a_matrix** é a matriz usada para calcular a média

### min
`int min(struct matrix a_matrix);`  
min retorna o menor elemento da matriz.
- **a_matrix** é a matriz onde o menor elemento será procurado

### max
`int max(struct matrix a_matrix);`  
max retorna o maior elemento da matriz.
- **a_matrix** é a matriz onde o maior elemento será procurado

## Função de multiplicação de matrizes 
 
 Implemente a seguinte função de multiplicação de matrizes:
 
`struct matrix matmul(struct matrix a_matrix, struct matrix b_matrix);`

## Entrega

- Será necessário criar o arquivo matrix.h com os protótipos das funções e a definição da struct;
- O arquivo matrix.c deverá conter as implementações das funções descritas neste documento;
- Os arquivos devem ser compactados e enviados para o e-mail petcc@ci.ufpb.br até às 23:59 horas do dia 12/09/2021;

## Critérios de avaliação

O projeto será avaliado através de testes que verificam a corretude funcional das funções implementadas.
Para tanto, o arquivo matrix.h será incluído em um script de teste, por isso, é fundamental que os protótipos das funções sigam exatamente as especificações apresentadas neste arquivo. Se isso não acontecer, o teste não funcionará.

## Observações
- Durante o desenvolvimento do projeto, um arquivo main.c deverá ser criado para testar as funções implementadas.































