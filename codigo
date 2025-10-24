#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <string.h>
#include <ctype.h>

#ifndef M_PI
#define M_PI 3.14159265358979323846
#endif

#define MAX_HISTORICO 10

typedef struct {
    char tipo[50];
    double a, b;
    double resultado;
    int id;
} Operacao;

Operacao historico[MAX_HISTORICO];
int contador_id = 1;
int indice_historico = 0;

void menu_principal();
void registrar_operacao(const char* tipo, double a, double b, double resultado);
void exibir_historico();
void exibir_matriz(int linhas, int colunas, int matriz[linhas][colunas]);
void ler_matriz(int linhas, int colunas, int matriz[linhas][colunas]);
void pausar_e_limpar();

double calc_adicao(double a, double b);
double calc_subtracao(double a, double b);
double calc_multiplicacao(double a, double b);
double calc_divisao(double a, double b);

long double factorial(int n);

void soma_matrizes_2x2();
void multiplicacao_matrizes_2x2();

void registrar_operacao(const char* tipo, double a, double b, double resultado) {
    historico[indice_historico].id = contador_id++;
    strcpy(historico[indice_historico].tipo, tipo);
    historico[indice_historico].a = a;
    historico[indice_historico].b = b;
    historico[indice_historico].resultado = resultado;

    indice_historico = (indice_historico + 1) % MAX_HISTORICO;
}

void exibir_historico() {
    printf("\n--- HISTORICO DAS ULTIMAS %d OPERACOES ---\n", MAX_HISTORICO);
    int inicio = (indice_historico) % MAX_HISTORICO;

    for (int i = 0; i < MAX_HISTORICO; i++) {
        int index = (inicio + i) % MAX_HISTORICO;

        if (historico[index].id > 0) {
            if (historico[index].b == 0 && (strcmp(historico[index].tipo, "Adicao") != 0 && strcmp(historico[index].tipo, "Subtracao") != 0 && strcmp(historico[index].tipo, "Multiplicacao") != 0 && strcmp(historico[index].tipo, "Divisao") != 0 && strcmp(historico[index].tipo, "Potencia") != 0 && strcmp(historico[index].tipo, "Percentagem") != 0 && strcmp(historico[index].tipo, "Soma Matriz 2x2") != 0)) {
                printf("[%03d] %s(%.2lf) = %.4lf\n", historico[index].id, historico[index].tipo, historico[index].a, historico[index].resultado);
            } else if (strcmp(historico[index].tipo, "Soma Matriz 2x2") == 0) {
                printf("[%03d] %s - Soma dos Elementos: %.4lf\n", historico[index].id, historico[index].tipo, historico[index].resultado);
            } else {
                printf("[%03d] %s: %.2lf e %.2lf = %.4lf\n", historico[index].id, historico[index].tipo, historico[index].a, historico[index].b, historico[index].resultado);
            }
        }
    }
    printf("--------------------------------------------\n");
}


void pausar_e_limpar() {
    printf("\nPressione ENTER para continuar...");
    while (getchar() != '\n');
    getchar();
    #ifdef _WIN32
        system("cls");
    #else
        system("clear");
    #endif
}

double calc_adicao(double a, double b) {
    return a + b;
}

double calc_subtracao(double a, double b) {
    return a - b;
}

double calc_multiplicacao(double a, double b) {
    return a * b;
}


double calc_divisao(double a, double b) {
    if (b == 0.0) {
        printf("Erro: Divisao por zero!\n");
        return NAN;
    }
    return a / b;
}


long double factorial(int n) {
    if (n < 0) return 0;
    if (n == 0) return 1;
    long double fact = 1.0;
    for (int i = 1; i <= n; ++i) {
        fact *= i;
    }
    return fact;
}


void exibir_matriz(int linhas, int colunas, int matriz[linhas][colunas]) {
    for (int i = 0; i < linhas; i++) {
        printf("|");
        for (int j = 0; j < colunas; j++) {
            printf(" %3d ", matriz[i][j]);
        }
        printf("|\n");
    }
}


void ler_matriz(int linhas, int colunas, int matriz[linhas][colunas]) {
    for (int i = 0; i < linhas; i++) {
        for (int j = 0; j < colunas; j++) {
            printf("M[%d][%d]: ", i + 1, j + 1);
            while (scanf("%d", &matriz[i][j]) != 1) {
                printf("Entrada invalida. Digite um numero inteiro para M[%d][%d]: ", i + 1, j + 1);
                while (getchar() != '\n');
            }
        }
    }
}


void soma_matrizes_2x2() {
    int A[2][2], B[2][2], C[2][2];
    double resultado_operacao = 0;

    printf("--- Soma de Matrizes 2x2 ---\n");
    printf("Digite os elementos da Matriz A:\n");
    ler_matriz(2, 2, A);
    printf("Digite os elementos da Matriz B:\n");
    ler_matriz(2, 2, B);

    printf("\nMatriz A:\n");
    exibir_matriz(2, 2, A);
    printf("\nMatriz B:\n");
    exibir_matriz(2, 2, B);

    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 2; j++) {
            C[i][j] = A[i][j] + B[i][j];
            resultado_operacao += C[i][j];
        }
    }

    printf("\nMatriz Resultado (A + B):\n");
    exibir_matriz(2, 2, C);

    registrar_operacao("Soma Matriz 2x2", 0, 0, resultado_operacao);
}

void menu_principal() {
    printf("\n===== CALCULADORA CIENTIFICA C (v2.0) =====\n");
    printf("--- B A S I C A S ---\n");
    printf(" 1. Adicao (+)\t\t 2. Subtracao (-)\n");
    printf(" 3. Multiplicacao (*)\t 4. Divisao (/)\n");
    printf("--- C I E N T I F I C A S ---\n");
    printf(" 5. Potencia (x^y)\t 6. Raiz Quadrada (sqrt)\n");
    printf(" 7. Fatorial (x!)\t 8. Logaritmo Natural (ln)\n");
    printf(" 9. Seno (sin, Graus)\t10. Cosseno (cos, Graus)\n");
    printf("... (11-19. Incluir Raizes, Log10, Inversas, Media, Mediana, etc.)\n");
    printf("--- M A T R I Z E S ---\n");
    printf("20. Soma Matrizes 2x2\t21. Multiplicacao Matrizes 2x2\n");
    printf("--- O U T R A S ---\n");
    printf("23. Exibir Historico\t24. Sair\n");
    printf("===========================================\n");
}


int main() {
    int escolha;
    double num1, num2, resultado;
    char tipo_operacao[50];

    for (int i = 0; i < MAX_HISTORICO; i++) {
        historico[i].id = 0;
    }

    do {
        menu_principal();
        printf("Digite o numero da sua escolha: ");

        if (scanf("%d", &escolha) != 1) {
            printf("Erro: Escolha invalida. Tente novamente.\n");
            while (getchar() != '\n');
            escolha = 0;
            continue;
        }

        switch (escolha) {
            case 1: case 2: case 3: case 4: case 5:
                printf("Digite o primeiro numero: ");
                scanf("%lf", &num1);
                printf("Digite o segundo numero: ");
                scanf("%lf", &num2);

                if (escolha == 1) {
                    resultado = calc_adicao(num1, num2);
                    strcpy(tipo_operacao, "Adicao");
                } else if (escolha == 2) {
                    resultado = calc_subtracao(num1, num2);
                    strcpy(tipo_operacao, "Subtracao");
                } else if (escolha == 3) {
                    resultado = calc_multiplicacao(num1, num2);
                    strcpy(tipo_operacao, "Multiplicacao");
                } else if (escolha == 4) {
                    resultado = calc_divisao(num1, num2);
                    strcpy(tipo_operacao, "Divisao");
                } else if (escolha == 5) {
                    resultado = pow(num1, num2);
                    strcpy(tipo_operacao, "Potencia");
                }

                if (!isnan(resultado)) {
                    printf("Resultado: %.4lf\n", resultado);
                    registrar_operacao(tipo_operacao, num1, num2, resultado);
                }
                break;

            case 6:
                printf("Digite o numero: ");
                scanf("%lf", &num1);
                if (num1 >= 0) {
                    resultado = sqrt(num1);
                    printf("Raiz Quadrada de %.2lf: %.4lf\n", num1, resultado);
                    registrar_operacao("Raiz Quadrada", num1, 0, resultado);
                } else {
                    printf("Erro: Nao existe raiz real de numero negativo.\n");
                }
                break;

            case 7:
                printf("Digite um inteiro nao negativo (max 20): ");
                int n;
                if (scanf("%d", &n) != 1 || floor((double)n) != n || n < 0 || n > 20) {
                     printf("Erro: Entrada invalida. Fatorial so e definido para inteiros nao negativos (limite 20).\n");
                } else {
                    resultado = factorial(n);
                    printf("O fatorial de %d e %Lf\n", n, (long double)resultado);
                    registrar_operacao("Fatorial", n, 0, resultado);
                }
                break;

            case 8:
                printf("Digite o numero: ");
                scanf("%lf", &num1);
                if (num1 > 0) {
                    resultado = log(num1);
                    printf("ln(%.2lf) = %.4lf\n", num1, resultado);
                    registrar_operacao("Log. Natural", num1, 0, resultado);
                } else {
                    printf("Erro: Logaritmo so e definido para numeros positivos.\n");
                }
                break;

            case 9:
                printf("Digite o angulo em Graus: ");
                scanf("%lf", &num1);
                resultado = sin(num1 * M_PI / 180.0);
                printf("sin(%.2lf graus) = %.4lf\n", num1, resultado);
                registrar_operacao("Seno (Graus)", num1, 0, resultado);
                break;

            case 10:
                printf("Digite o angulo em Graus: ");
                scanf("%lf", &num1);
                resultado = cos(num1 * M_PI / 180.0);
                printf("cos(%.2lf graus) = %.4lf\n", num1, resultado);
                registrar_operacao("Cosseno (Graus)", num1, 0, resultado);
                break;

            case 11: case 12: case 13: case 14: case 15: case 16: case 17: case 18: case 19:
                printf("Opcao %d ainda nao implementada.\n", escolha);
                break;

            case 20:
                soma_matrizes_2x2();
                break;

            case 21:
                printf("Opcao de Multiplicacao de Matrizes ainda nao implementada.\n");
                break;

            case 23:
                exibir_historico();
                break;

            case 24:
                printf("Saindo da Calculadora. Ate mais!\n");
                break;

            default:
                printf("Erro: Opcao invalida. Por favor, escolha um numero entre 1 e 24.\n");
        }

        if (escolha != 24) {
            pausar_e_limpar();
        }

    } while (escolha != 24);

    return EXIT_SUCCESS;
}
