#include <stdio.h> // Para funções de entrada/saída como printf e scanf
#include <string.h> // Para funções de manipulação de strings como strlen e strtok

// Definição da estrutura para armazenar os dados de uma cidade
typedef struct {
    char estado[50];
    char codigo[50];
    char nomeCidade[100];
    unsigned long int populacao; // Alterado para unsigned long int
    float area; // em km²
    float pib; // em bilhões de reais
    int pontosTuristicos;
    float densidadePopulacional; // Calculado
    float pibPerCapita; // Calculado
    float superPoder; // Calculado
} Cidade;

// Função para limpar o buffer de entrada
void limparBuffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF);
}

// Função para ler os dados de uma cidade
void lerDadosCidade(Cidade *cidade, int numeroCarta) {
    printf("\n--- Dados da Carta %d ---\n", numeroCarta);

    printf("Estado: ");
    fgets(cidade->estado, sizeof(cidade->estado), stdin);
    strtok(cidade->estado, "\n"); // Remove o caractere de nova linha

    printf("Código da Carta: ");
    fgets(cidade->codigo, sizeof(cidade->codigo), stdin);
    strtok(cidade->codigo, "\n");

    printf("Nome da Cidade: ");
    fgets(cidade->nomeCidade, sizeof(cidade->nomeCidade), stdin);
    strtok(cidade->nomeCidade, "\n");

    printf("População: ");
    scanf("%lu", &cidade->populacao); // %lu para unsigned long int
    limparBuffer(); // Limpa o buffer após scanf

    printf("Área (em km²): ");
    scanf("%f", &cidade->area);
    limparBuffer(); // Limpa o buffer após scanf

    printf("PIB (em bilhões de reais): ");
    scanf("%f", &cidade->pib);
    limparBuffer(); // Limpa o buffer após scanf

    printf("Número de Pontos Turísticos: ");
    scanf("%d", &cidade->pontosTuristicos);
    limparBuffer(); // Limpa o buffer após scanf
}

// Função para calcular a densidade populacional e o PIB per capita
void calcularMetricasCidade(Cidade *cidade) {
    // Calcula a Densidade Populacional
    if (cidade->area > 0) {
        cidade->densidadePopulacional = (float)cidade->populacao / cidade->area;
    } else {
        cidade->densidadePopulacional = 0.0; // Evita divisão por zero
    }

    // Calcula o PIB per Capita
    if (cidade->populacao > 0) {
        cidade->pibPerCapita = (cidade->pib * 1000000000.0) / (float)cidade->populacao;
    } else {
        cidade->pibPerCapita = 0.0; // Evita divisão por zero
    }
}

// Função para calcular o Super Poder
void calcularSuperPoder(Cidade *cidade) {
    float inversoDensidade = (cidade->densidadePopulacional != 0) ? (1.0 / cidade->densidadePopulacional) : 0.0; // Evita divisão por zero

    cidade->superPoder = (float)cidade->populacao + cidade->area + cidade->pib +
                        cidade->pontosTuristicos + cidade->pibPerCapita + inversoDensidade;
}

// Função para exibir os dados de uma cidade
void exibirDadosCidade(const Cidade *cidade, int numeroCarta) {
    printf("\n--- Carta %d ---\n", numeroCarta);
    printf("Estado: %s\n", cidade->estado);
    printf("Código: %s\n", cidade->codigo);
    printf("Nome da Cidade: %s\n", cidade->nomeCidade);
    printf("População: %lu\n", cidade->populacao); // %lu para unsigned long int
    printf("Área: %.2f km²\n", cidade->area);
    printf("PIB: %.2f bilhões de reais\n", cidade->pib);
    printf("Número de Pontos Turísticos: %d\n", cidade->pontosTuristicos);
    printf("Densidade Populacional: %.2f hab/km²\n", cidade->densidadePopulacional);
    printf("PIB per Capita: %.2f reais\n", cidade->pibPerCapita);
    printf("Super Poder: %.2f\n", cidade->superPoder);
}

// Função para comparar as cartas e exibir os resultados
void compararCartas(const Cidade *cidade1, const Cidade *cidade2) {
    printf("\nComparação de Cartas:\n");

    printf("População: Carta %d venceu (%d)\n", (cidade1->populacao >= cidade2->populacao) ? 1 : 2, (cidade1->populacao >= cidade2->populacao) ? 1 : 0);
    printf("Área: Carta %d venceu (%d)\n", (cidade1->area >= cidade2->area) ? 1 : 2, (cidade1->area >= cidade2->area) ? 1 : 0);
    printf("PIB: Carta %d venceu (%d)\n", (cidade1->pib >= cidade2->pib) ? 1 : 2, (cidade1->pib >= cidade2->pib) ? 1 : 0);
    printf("Pontos Turísticos: Carta %d venceu (%d)\n", (cidade1->pontosTuristicos >= cidade2->pontosTuristicos) ? 1 : 2, (cidade1->pontosTuristicos >= cidade2->pontosTuristicos) ? 1 : 0);
    printf("Densidade Populacional: Carta %d venceu (%d)\n", (cidade1->densidadePopulacional <= cidade2->densidadePopulacional) ? 1 : 2, (cidade1->densidadePopulacional <= cidade2->densidadePopulacional) ? 1 : 0);
    printf("PIB per Capita: Carta %d venceu (%d)\n", (cidade1->pibPerCapita >= cidade2->pibPerCapita) ? 1 : 2, (cidade1->pibPerCapita >= cidade2->pibPerCapita) ? 1 : 0);
    printf("Super Poder: Carta %d venceu (%d)\n", (cidade1->superPoder >= cidade2->superPoder) ? 1 : 2, (cidade1->superPoder >= cidade2->superPoder) ? 1 : 0);
}

int main() {
    Cidade cidade1; // Declaração da primeira cidade
    Cidade cidade2; // Declaração da segunda cidade

    // Leitura dos dados para a primeira cidade
    lerDadosCidade(&cidade1, 1);
    // Cálculo das métricas para a primeira cidade
    calcularMetricasCidade(&cidade1);
    // Cálculo do Super Poder para a primeira cidade
    calcularSuperPoder(&cidade1);

    // Leitura dos dados para a segunda cidade
    lerDadosCidade(&cidade2, 2);
    // Cálculo das métricas para a segunda cidade
    calcularMetricasCidade(&cidade2);
    // Cálculo do Super Poder para a segunda cidade
    calcularSuperPoder(&cidade2);

    // Exibição dos dados de ambas as cidades
    exibirDadosCidade(&cidade1, 1);
    exibirDadosCidade(&cidade2, 2);

    // Comparação das cartas
    compararCartas(&cidade1, &cidade2);

    return 0; // Indica que o programa foi executado com sucesso
}
