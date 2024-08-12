# An-lise-de-Performance-de-A-es-e-Compara-o-de-Investimentos
Análise de Performance de Ações e Comparação de Investimentos


### Temos o preço de diferentes ações no início de 2024 e em maio de 2024, queremos:
    - Ação que mais subiu, ação que mais caiu no período (percentualmente)
    - Se tivessemos 1.000 reais investido em um portfólio com as ações da carteira A vs um portfólio com as ações B, qual teria rendido mais? - considere que os 1.000 reais são investidos de forma proporcional entre cada ativo da carteira

    acoes = {
    "PETR4": [37.78, 37.01],
    "VALE3": [77.05, 65.30],
    "ITUB4": [33.52, 33.74],
    "ABEV3": [13.71, 11.81],
    "WEGE3": [36.57, 38.35],
    "BBAS3": [27.38, 29.41],
    "JBSS3": [25.17, 29.96],
    "SBSP3": [73.63, 75.07]
}

carteiraA = ["PETR4", "VALE3", "JBSS3", "SBSP3"]
carteiraB = ["WEGE3", "BBAS3", "ITUB4", "ABEV3"]

acao_mais_subiu = ""
percentual_mais_subiu = 0
acao_mais_caiu = ""
percentual_mais_caiu = 0

for acao in acoes:
    precos = acoes[acao]
    preco_inicio = precos[0]
    preco_fim = precos[1]
    variacao_percentual = preco_fim / preco_inicio - 1
    if variacao_percentual > percentual_mais_subiu:
        acao_mais_subiu = acao
        percentual_mais_subiu = variacao_percentual
    elif variacao_percentual < percentual_mais_caiu:
        acao_mais_caiu = acao
        percentual_mais_caiu = variacao_percentual

print(acao_mais_subiu, f"Subiu {percentual_mais_subiu}")
print(acao_mais_caiu, f"Caiu {percentual_mais_caiu}")

variacoes = {}

for acao in acoes:
    precos = acoes[acao]
    preco_inicio = precos[0]
    preco_fim = precos[1]
    variacao_percentual = preco_fim / preco_inicio - 1
    variacoes[acao] = variacao_percentual

print(variacoes)

valor_investido = 1000 / len(carteiraA)
valor_total_carteiraA = 0
valor_total_carteiraB = 0
for acao in carteiraA:
    valor_final_acao = variacoes[acao] * valor_investido + valor_investido
    valor_total_carteiraA += valor_final_acao
for acao in carteiraB:
    valor_final_acao = variacoes[acao] * valor_investido + valor_investido
    valor_total_carteiraB += valor_final_acao

print(valor_total_carteiraA)
print(valor_total_carteiraB)
