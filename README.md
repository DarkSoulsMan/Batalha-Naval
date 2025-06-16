# Batalha-Naval

1. Introdução
Este trabalho apresenta a implementação do jogo Batalha Naval em linguagem C, desenvolvido como requisito parcial da disciplina de Programação Estruturada. O objetivo foi consolidar os conhecimentos em manipulação de matrizes, estruturas de dados e funções, criando uma versão simplificada do clássico jogo de estratégia naval.

2. Desenvolvimento
2.1. Estruturas de Dados
O jogo utiliza três matrizes 10x10 para representar:

tabuleiroJogador: Armazena a frota do jogador

tabuleiroComputador: Armazena a frota do computador (visão real)

tabuleiroVisivel: Mostra ao jogador seus acertos/erros contra o computador

A estrutura Navio define os tipos de embarcações:

c
typedef struct {
    int tamanho;     // Número de casas ocupadas (2-5)
    int quantidade;  // Quantidade de cada tipo na frota
} Navio;
2.2. Lógica Principal
Inicialização
Tabuleiros preenchidos com '~' (água)

Frota automática com:

1 Porta-aviões (5 casas)

1 Couraçado (4 casas)

2 Contratorpedeiros (3 casas)

1 Submarino (2 casas)

Fluxo do Jogo
Turno do Jogador:

Conversão de coordenadas (ex: "A1" → [0][0])

Verificação de acerto ('X') ou erro ('O')

Turno do Computador:

Jogadas aleatórias com prevenção de repetição

Condições de Vitória
Verificação se todos os 'N' (navios) foram substituídos por 'X' (atingidos).

3. Implementação
Funções Principais
Função	Descrição
inicializarTabuleiro()	Preenche matriz com água
mostrarTabuleiro()	Exibe tabuleiro formatado
posicionarFrotaAutomaticamente()	Distribui navios aleatoriamente
disparar()	Executa jogada e atualiza tabuleiros
Exemplo de Código
c
bool disparar(char tabuleiro[TAM][TAM], int linha, int coluna) {
    if (tabuleiro[linha][coluna] == 'N') {
        tabuleiro[linha][coluna] = 'X'; // Acerto
        return true;
    } else {
        tabuleiro[linha][coluna] = 'O'; // Erro
        return false;
    }
}
4. Testes Realizados
Cenário	Entrada	Resultado
Tiro válido na água	"B5"	'O' no tabuleiro
Tiro válido em navio	"D3"	'X' no tabuleiro
Coordenada inválida	"Z9"	Mensagem de erro
Tiro repetido	"A1" (já atingido)	Jogada ignorada

5. Conclusão
O projeto atingiu os objetivos propostos, demonstrando:
- Domínio de matrizes e estruturas
- Implementação de lógica condicional
- Validação de entrada do usuário

Dificuldades Encontradas:

Gerenciamento de posicionamento automático sem sobreposição

Controle de turnos alternados

Melhorias Futuras:

Interface gráfica com ncurses

Sistema de pontuação

Diferentes níveis de dificuldade
