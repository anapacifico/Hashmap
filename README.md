# Hashmap
Trabalho final - Implementação de um sistema de reserva de hotéis utilizando Hashmap. 


Para este projeto A3.2, deveremos construir um sistema de reservas de hotéis, onde a eficiência na busca, inserção e remoção de reservas é crucial. O hashmap pode ser usado para mapear o número de identificação da reserva (como chave) para os detalhes da reserva (como valor).


A chave de cada reserva deverá ser gerada a partir de um número inteiro ou string Alpha Numérica que representa o número da reserva.

Cada reserva deverá conter os seguintes valores:

Nome do Hotel
Numero do Quarto
Data de Check-In
Data de Check-Out
O uso do hashmap deverá permitir:

Inserir novas reservas de forma eficiente.
Recuperar detalhes de uma reserva rapidamente usando o código da reserva.
Remover reservas de forma eficiente após o check-out ou cancelamento
Uma função hash ORIGINAL deverá ser criada. As colisões deverão ser tratadas como possíveis reservas em caso de cancelamento, ou seja, se um reserva for cancelada a primeira colisão deverá assumir a reserva (defina bem sua estratégia de tratamento de colisão).

O projeto deverá ser entregue através do ULife em pacote único.

A função hash baseia-se no princípio de embaralhamento, para que assim, produzaum número de hash único para cada registro.

A função recebe alguns valores de entrada......

A função incia-se com algumas declarações: int hash = Variável na qual será armazenada o valor de hash após algumas misturas e embaralhamentos char atual = Váriavel que armazena o caracter atual da chave. char proximo = Váriavel que armazena o próximo caracter da chave.

Após as declarações, inicia-se um loop for que percorre de 0 até o tamanho da chave - 1. (para garantir que o loop não acesse algum caracter de fora da palavra, gerando erros de index.).

Ao entrar no loop, a variável atual recebe o índice do primeiro caracter da palavra. A variável próximo recebe o indíce + 1, que é o segundo caracter da palavra.

A linha:

hash += ((int) atual * (i+1) * (i + 2) * (int) proximo)

    Transforma o valor de atual (char) em um tipo inteiro (int), para que seja feita as operações. Após a transformação, vem as operações. 

    (int) atual * (i + 1) * (i + 2) * (int) próximo = valor atua * segundo caracter * terceiro caracter * o valor armazendao na variável próximo. 

hash += ((hash << 5) + hash >> 10) + (int) atual;

    Utiliza de deslocamento de bits para fazer o embaralhamento

    pega o valor armazenado em "hash", desloca 5 bits para a esquerda e depois soma com o valor de "hash" deslocado 10 bits a direita. Após esse embaralhamento soma-se o valor que está armazenado na variável "atual". 

hash += (hash << 5) ^ (hash >> 28) ^ seed ^ (int) atual;

    Este trecho continua usando deslocamento de bits para embaralhamento. 

    o diferencial deste trecho é o operador ^ (XOR) que contribui ainda mais com o embaralhamento. 

    Além do operador XOR, este trecho introduz o uso da variável seed. Uma semente usada para garantir o embaralhamento. 
Após isso, o loop for é encerrado.

Depois, é feito uma sequência de operações, utilizando este mesmo princípio: hash += (hash << 5) ^ (hash >> 28) ^ seed ^ (int) atual; Apenas alterando a quantidade de deslocamento.

Para encerrar, a função tem um return que garante que os valores estejam dentro do tamanho do vetor, utilizando o hash % tam
