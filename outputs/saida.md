![como funciona uma IA generativa?](https://github.com/user-attachments/assets/baeb46e5-7ec2-4dae-8412-99df49a46461)
-
![Quais são as limitações da IA generativa?](https://github.com/user-attachments/assets/2a35db3e-1832-477f-bed1-be59ab1994db)
-
![como funciona a separação de dados para treinamento de um modelo de IA?](https://github.com/user-attachments/assets/9127c38f-4abd-4cd2-90a1-cbea5e5d0dcf)
-
faça um jogo da velha em c#

Aqui está um exemplo de código em C# para um jogo da velha simples no console. Ele permite que dois jogadores se alternem para marcar seus movimentos e determina o vencedor com base nas regras clássicas do jogo.

csharp
using System;

class JogoDaVelha
{
    static char[,] tabuleiro = {
        { '1', '2', '3' },
        { '4', '5', '6' },
        { '7', '8', '9' }
    };
    static char jogadorAtual = 'X';

    static void Main()
    {
        int movimentos = 0;
        bool vitoria = false;

        while (movimentos < 9 && !vitoria)
        {
            Console.Clear();
            ExibirTabuleiro();
            Console.WriteLine($"Jogador {jogadorAtual}, escolha uma posição:");

            string entrada = Console.ReadLine();
            if (int.TryParse(entrada, out int escolha) && escolha >= 1 && escolha <= 9)
            {
                if (MarcarPosicao(escolha))
                {
                    movimentos++;
                    vitoria = VerificarVencedor();
                    jogadorAtual = jogadorAtual == 'X' ? 'O' : 'X';
                }
                else
                {
                    Console.WriteLine("Posição já ocupada! Aperte Enter para tentar novamente.");
                    Console.ReadLine();
                }
            }
            else
            {
                Console.WriteLine("Entrada inválida! Aperte Enter para tentar novamente.");
                Console.ReadLine();
            }
        }

        Console.Clear();
        ExibirTabuleiro();
        Console.WriteLine(vitoria ? $"Jogador {jogadorAtual} venceu!" : "Empate!");
    }

    static void ExibirTabuleiro()
    {
        Console.WriteLine($" {tabuleiro[0, 0]} | {tabuleiro[0, 1]} | {tabuleiro[0, 2]} ");
        Console.WriteLine("---|---|---");
        Console.WriteLine($" {tabuleiro[1, 0]} | {tabuleiro[1, 1]} | {tabuleiro[1, 2]} ");
        Console.WriteLine("---|---|---");
        Console.WriteLine($" {tabuleiro[2, 0]} | {tabuleiro[2, 1]} | {tabuleiro[2, 2]} ");
    }

    static bool MarcarPosicao(int escolha)
    {
        for (int i = 0; i < 3; i++)
        {
            for (int j = 0; j < 3; j++)
            {
                if (tabuleiro[i, j] == escolha.ToString()[0])
                {
                    tabuleiro[i, j] = jogadorAtual;
                    return true;
                }
            }
        }
        return false;
    }

    static bool VerificarVencedor()
    {
        for (int i = 0; i < 3; i++)
        {
            if (tabuleiro[i, 0] == tabuleiro[i, 1] && tabuleiro[i, 1] == tabuleiro[i, 2]) return true;
            if (tabuleiro[0, i] == tabuleiro[1, i] && tabuleiro[1, i] == tabuleiro[2, i]) return true;
        }

        if (tabuleiro[0, 0] == tabuleiro[1, 1] && tabuleiro[1, 1] == tabuleiro[2, 2]) return true;
        if (tabuleiro[0, 2] == tabuleiro[1, 1] && tabuleiro[1, 1] == tabuleiro[2, 0]) return true;

        return false;
    }
}
Esse código cria um jogo da velha interativo no console. Ele verifica se um jogador ganhou após cada movimento e alterna entre os jogadores 'X' e 'O'.

Quer que eu adicione alguma funcionalidade extra, como um modo de jogador contra IA? Posso melhorar isso para você!



