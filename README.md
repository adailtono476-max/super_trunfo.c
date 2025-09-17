# super_trunfo.c
Meu projeto
#include <stdio.h>
#include <string.h>

// Estrutura para representar uma carta do Super Trunfo
typedef struct {
    char estado; // Letra de 'A' a 'H'
    char codigo[5]; // Ex: "A01"
    char nome_cidade[50]; // Nome da cidade
    int populacao; // Número de habitantes
    float area_km2; // Área em km²
    float pib_bilhoes; // PIB em bilhões de reais
    int pontos_turisticos; // Quantidade de pontos turísticos
} CartaSuperTrunfo;

int main() {
    // Declaração de duas cartas
    CartaSuperTrunfo carta1, carta2;

    // --- Coleta de dados para a Carta 1 ---
    printf("\n--- CADASTRO DA CARTA 1 ---\n");

    printf("Digite o Estado (A-H): ");
    scanf(" %c", &carta1.estado); // Note o espaço antes de %c para consumir o newline anterior

    printf("Digite o Código da Carta (ex: A01): ");
    scanf("%s", carta1.codigo);

    printf("Digite o Nome da Cidade: ");
    scanf("%s", carta1.nome_cidade);

    printf("Digite a População: ");
    scanf("%d", &carta1.populacao);

    printf("Digite a Área (em km²): ");
    scanf("%f", &carta1.area_km2);

    printf("Digite o PIB (em bilhões de reais): ");
    scanf("%f", &carta1.pib_bilhoes);

    printf("Digite o Número de Pontos Turísticos: ");
    scanf("%d", &carta1.pontos_turisticos);

    // --- Coleta de dados para a Carta 2 ---
    printf("\n--- CADASTRO DA CARTA 2 ---\n");

    printf("Digite o Estado (A-H): ");
    scanf(" %c", &carta2.estado);

    printf("Digite o Código da Carta (ex: A01): ");
    scanf("%s", carta2.codigo);

    printf("Digite o Nome da Cidade: ");
    scanf("%s", carta2.nome_cidade);

    printf("Digite a População: ");
    scanf("%d", &carta2.populacao);

    printf("Digite a Área (em km²): ");
    scanf("%f", &carta2.area_km2);

    printf("Digite o PIB (em bilhões de reais): ");
    scanf("%f", &carta2.pib_bilhoes);

    printf("Digite o Número de Pontos Turísticos: ");
    scanf("%d", &carta2.pontos_turisticos);

    // --- Exibição das informações da Carta 1 ---
    printf("\n\n======= DETALHES DA CARTA 1 =======\n");
    printf("Estado: %c\n", carta1.estado);
    printf("Código: %s\n", carta1.codigo);
    printf("Nome da Cidade: %s\n", carta1.nome_cidade);
    printf("População: %d\n", carta1.populacao);
    printf("Área: %.2f km²\n", carta1.area_km2);
    printf("PIB: %.2f bilhões de reais\n", carta1.pib_bilhoes);
    printf("Número de Pontos Turísticos: %d\n", carta1.pontos_turisticos);

    // --- Exibição das informações da Carta 2 ---
    printf("\n\n======= DETALHES DA CARTA 2 =======\n");
    printf("Estado: %c\n", carta2.estado);
    printf("Código: %s\n", carta2.codigo);
    printf("Nome da Cidade: %s\n", carta2.nome_cidade);
    printf("População: %d\n", carta2.populacao);
    printf("Área: %.2f km²\n", carta2.area_km2);
    printf("PIB: %.2f bilhões de reais\n", carta2.pib_bilhoes);
    printf("Número de Pontos Turísticos: %d\n", carta2.pontos_turisticos);

    return 0;
}

