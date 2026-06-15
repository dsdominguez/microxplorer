# MicroXplorer

Protótipo de tomografia computadorizada (TC) de raios X desenvolvido no **CPqCTR**, **CCAM** e **UESC**.

---

## Sobre o projeto

O **MicroXplorer** é um sistema experimental de TC de raios X de baixo custo, construído para aquisição e reconstrução de amostras diversas — desde objetos biológicos até materiais de construção civil.

**Portal de download das amostras:** [MicroexplorerPage](https://antonio-hos.github.io/MicroexplorerPage/)

---

## Estrutura experimental (hardware)

O sistema utiliza os seguintes componentes:

| Componente | Equipamento |
|---|---|
| **Detector** | X-PANEL 1412i (1400 × 1200 px, 14 bits) |
| **Fonte de raios X** | Tubo Mini-X2 |
| **Controle de rotação** | Arduino Uno + motor de passo |
| **Estrutura mecânica** | Perfis metálicos (base e suporte do conjunto) |

<p align="center">
  <img src="./docs/images/prototipo.jpeg" alt="Protótipo MicroXplorer" width="700"/>
</p>

### Fluxo de aquisição

1. Posicionar a amostra no eixo de rotação (motor de passo).
2. Acionar a fonte Mini-X2 e capturar projeções com o detector X-PANEL 1412i.
3. Registrar imagens de calibração (**dark** e **flat**).
4. Processar e reconstruir os dados com ferramentas como [TIGRE](https://github.com/CERN/TIGRE).

---

## Mapa do repositório

```
microxplorer/
├── README.md
├── docs/
│   └── images/              # Fotos do equipamento e amostras
├── ProcessSapinhosVitor/    # Notebooks de pós-processamento (Sapinho)
├── TC01_Caracol_202509/
├── TC02_Cachimbo_Arquiometria_20251013/
├── TC03_Sapinho_20251028/
├── TC04_DisciplinaTC_PhoneOuvido_20251216/
├── TC05_DisciplinaTC_Abobora_20251216/
├── TC06_Concreto_Isopor/
├── TC07_Concreto_Isopor_2/
├── TC08_FlatMassivo/
├── TC09_Concreto_Isopor_3/
├── TC10_Concreto_Argila_Expandida_1/
├── TC11_Concreto_Argila_Expandida_2/
├── TC12_Concreto_Ref_1/
└── TC13_Concreto_Ref_2/
```

---

## Pastas e experimentos

Cada pasta `TCxx_*` contém dados brutos de aquisição. A estrutura interna típica inclui:

- `*prjs/` — projeções (`.txt` com metadados + `.dat` com dados brutos)
- `dark/` ou `dark*.txt` — calibração dark
- `flat/` ou `flat*.txt` — calibração flat
- `data.txt` — parâmetros geométricos (SDD, SOD, ODD)
- `python/` — notebooks de visualização (quando disponível)

### TC01 — Caracol (set/2025)

| Pasta | `TC01_Caracol_202509` |
|---|---|
| **Amostra** | Caracol |
| **Projeções** | 5, 100 e 200 projeções |
| **Geometria** | ODD 10 cm; SDD 52–54,6 cm |
| **Extras** | `python/createVideo.ipynb` |

### TC02 — Cachimbo / Arqueometria (out/2025)

| Pasta | `TC02_Cachimbo_Arquiometria_20251013` |
|---|---|
| **Amostra** | Cachimbo (estudo arqueométrico) |
| **Projeções** | 10 e 400 projeções |
| **Geometria** | SDD 58,5–59 cm; SOD 49,0–49,5 cm |
| **Extras** | `python/createVideo.ipynb`, `distancias.txt` |

### TC03 — Sapinho (out/2025)

| Pasta | `TC03_Sapinho_20251028` |
|---|---|
| **Amostra** | Sapinho |
| **Projeções** | 10 e 400 projeções |
| **Extras** | `python/createVideo.ipynb`, filtros de flat em `flat__Filtering/` |

### TC04 — Disciplina TC: Phone/Ouvido (dez/2025)

| Pasta | `TC04_DisciplinaTC_PhoneOuvido_20251216` |
|---|---|
| **Amostra** | Celular / ouvido (experimento da disciplina) |
| **Projeções** | 400 projeções (`PhoneOuvido400Prjs/`) |
| **Calibração** | `darkflat/` |

### TC05 — Disciplina TC: Abóbora (dez/2025)

| Pasta | `TC05_DisciplinaTC_Abobora_20251216` |
|---|---|
| **Amostra** | Abóbora (experimento da disciplina) |
| **Projeções** | 12 e 400 projeções (`abobora12Prjs/`, `abobora400Prjs/`) |
| **Calibração** | `darkflat/` |

### TC06 — Concreto com Isopor

| Pasta | `TC06_Concreto_Isopor` |
|---|---|
| **Amostra** | Concreto com agregado de Isopor |
| **Geometria** | SDD 57,3 cm; SOD 37,0 cm |

### TC07 — Concreto com Isopor (amostra 2)

| Pasta | `TC07_Concreto_Isopor_2` |
|---|---|
| **Amostra** | CP — Ø 21 mm, altura 49 mm |
| **Geometria** | ODD 6,8 cm; SDD 57,3 cm; SOD 50,5 cm |

### TC08 — Flat massivo

| Pasta | `TC08_FlatMassivo` |
|---|---|
| **Finalidade** | Calibração flat em campo amplo (~200 projeções) |
| **Conteúdo** | Projeções, dark e flat de referência |

### TC09 — Concreto com Isopor (amostra 3)

| Pasta | `TC09_Concreto_Isopor_3` |
|---|---|
| **Amostra** | Concreto com Isopor — amostra 2 |
| **Observação** | Condições similares ao TC07 (`readme.txt`) |

### TC10 — Concreto com Argila Expandida (1)

| Pasta | `TC10_Concreto_Argila_Expandida_1` |
|---|---|
| **Amostra** | Concreto com argila expandida |

### TC11 — Concreto com Argila Expandida (2)

| Pasta | `TC11_Concreto_Argila_Expandida_2` |
|---|---|
| **Amostra** | Concreto com argila expandida (segunda amostra) |

### TC12 — Concreto de referência (1)

| Pasta | `TC12_Concreto_Ref_1` |
|---|---|
| **Amostra** | Concreto de referência |

### TC13 — Concreto de referência (2)

| Pasta | `TC13_Concreto_Ref_2` |
|---|---|
| **Amostra** | Concreto de referência (segunda amostra) |

### ProcessSapinhosVitor

| Pasta | `ProcessSapinhosVitor` |
|---|---|
| **Finalidade** | Pós-processamento dos dados do Sapinho (TC03) |
| **Conteúdo** | `LoadSaveAs_mhd.ipynb` — exportação para formato MHD |

---

## Formato dos dados

Cada arquivo `.txt` de projeção contém metadados do detector:

```
ImageFileName=img1.dat
SerialNumber=3000030367-23380001
Width=1400
Height=1200
PixelDepth=14
GainRange=LFW
BinningMode=1x1
```

Os dados brutos ficam nos arquivos `.dat` correspondentes.


## Instituições

| Sigla | Nome |
|---|---|
| **CPqCTR** | Centro de Pesquisas em Ciências e Tecnologias das Radiações |
| **CCAM** | Centro de Computação Avançada e Multidisciplinar |
| **UESC** | Universidade Estadual de Santa Cruz |

---

## Referências

- **TIGRE** — *Tomographic Iterative GPU-based Reconstruction Toolbox*  
  https://github.com/CERN/TIGRE
