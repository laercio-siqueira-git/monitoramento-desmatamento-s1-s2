# Monitoramento de desmatamento com Sentinel-1 (SAR) e Sentinel-2 (óptico)

Piloto de detecção de desmatamento na Amazônia que combina radar e imagem óptica, com validação espacial e entrega como alertas georreferenciados.

> **Status:** piloto em execução. Esta página será atualizada com os resultados (métricas, mapa de alertas e figuras de antes e depois).

## Pergunta

Quanto o radar (SAR) acrescenta à imagem óptica na detecção de desmatamento numa região onde a nuvem cobre boa parte do ano?

## Abordagem

- **Área-piloto:** cerca de 27 × 27 km no arco do desmatamento, escolhida automaticamente entre áreas candidatas.
- **Dados:** Sentinel-2 SR Harmonized com máscara de nuvem Cloud Score+ e Sentinel-1 GRD (VV, VH), em composições medianas de estação seca antes e depois.
- **Rótulo:** perda florestal anual do Hansen Global Forest Change v1.12, restrita à floresta remanescente no início do período.
- **Modelos:** Random Forest no Google Earth Engine, comparando só óptico, só SAR e fusão.
- **Validação:** holdout espacial (treino numa metade da área, teste na outra), avaliando todos os pixels de floresta da metade de teste.
- **Entrega:** alertas em polígonos com área (ha), probabilidade média e concordância com a referência, em GeoJSON, CSV e mapa HTML.

## Como reproduzir

1. Registre um projeto do Google Cloud no Earth Engine para uso não comercial.
2. Abra `piloto_desmatamento_s1_s2.ipynb` no Google Colab ou no Jupyter local.
3. Defina a variável de ambiente `EE_PROJECT` com o ID do projeto (ou escreva-o em `PROJECT_ID`) e execute todas as células.

## Dados e créditos

- Contém dados modificados do Copernicus Sentinel (Sentinel-1 e Sentinel-2), processados no Google Earth Engine.
- Cloud Score+: Pasquarella et al. (2023), CVPR Workshops.
- Hansen, M. C. et al. (2013). High-Resolution Global Maps of 21st-Century Forest Cover Change. *Science* 342, 850–853. Versão 1.12 (2000–2024).

## Autor

Laércio Siqueira, cientista de dados.
