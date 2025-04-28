# Recursos-de-IA-Generativa-com-Copilot-e-OpenAI
Recursos de IA Generativa com Copilot e OpenAI

# Função para exibir o tabuleiro
def exibir_tabuleiro(tabuleiro):
    for linha in tabuleiro:
        print("|".join(linha))
    print()

# Função para verificar se há um vencedor
def verificar_vencedor(tabuleiro, jogador):
    # Verifica linhas, colunas e diagonais
    for i in range(3):
        if all(tabuleiro[i][j] == jogador for j in range(3)) or all(tabuleiro[j][i] == jogador for j in range(3)):
            return True
    if all(tabuleiro[i][i] == jogador for i in range(3)) or all(tabuleiro[i][2-i] == jogador for i in range(3)):
        return True
    return False

# Função principal
def jogo_da_velha():
    # Inicializa o tabuleiro
    tabuleiro = [[" " for _ in range(3)] for _ in range(3)]
    jogador_atual = "X"
    movimentos_restantes = 9

    while movimentos_restantes > 0:
        exibir_tabuleiro(tabuleiro)
        print(f"Jogador {jogador_atual}, é a sua vez!")

        # Solicita a entrada do jogador
        try:
            linha = int(input("Escolha a linha (0, 1, 2): "))
            coluna = int(input("Escolha a coluna (0, 1, 2): "))
        except ValueError:
            print("Por favor, insira números válidos.")
            continue

        # Verifica se a posição é válida
        if linha < 0 or linha > 2 or coluna < 0 or coluna > 2 or tabuleiro[linha][coluna] != " ":
            print("Movimento inválido! Tente novamente.")
            continue

        # Faz o movimento
        tabuleiro[linha][coluna] = jogador_atual
        movimentos_restantes -= 1

        # Verifica se há um vencedor
        if verificar_vencedor(tabuleiro, jogador_atual):
            exibir_tabuleiro(tabuleiro)
            print(f"Parabéns, jogador {jogador_atual}! Você venceu!")
            return

        # Troca de jogador
        jogador_atual = "O" if jogador_atual == "X" else "X"

    exibir_tabuleiro(tabuleiro)
    print("Empate! Ninguém venceu.")

# Inicia o jogo
jogo_da_velha()

![image](https://github.com/user-attachments/assets/b79a926e-e47f-40ea-a0ac-9bb66a3abac3)


