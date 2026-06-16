# SAD AHP — Priorização Hierárquica Matricial

Este repositório é o módulo independente do ecossistema **SAD MCDM**, configurado para operar exclusivamente com o método **AHP (Analytic Hierarchy Process)**.

---

## 🎨 Identidade Visual e Branding
- **Nome Oficial:** SAD AHP
- **Cores Oficiais:** Dourado (`#D97706`) e Grafite (`#4B5563`)
- **Conceito Visual:** Árvore hierárquica de decisão representando as ramificações de múltiplos níveis de critérios.
- **Copyright:** Direitos Reservados © 2026 SAD-MCDM. Todos os direitos reservados.

---

## 🧠 Formulação Matemática e Funcionamento

O método AHP (desenvolvido por Thomas Saaty) baseia-se na decomposição do problema em hierarquias e na avaliação par a par de atratividade e importância usando uma escala semântica fundamental de 1 a 9.

### 1. Escala de Saaty
* $1$: Igual importância
* $3$: Moderada importância de um sobre o outro
* $5$: Forte importância
* $7$: Muito forte ou demonstrada importância
* $9$: Importância extrema

### 2. Matriz de Comparações Par a Par ($A$)
Seja $A = [a_{ij}]$ a matriz de julgamentos de dimensão $n \times n$:
$$A = \begin{pmatrix} 
1 & a_{12} & \cdots & a_{1n} \\ 
a_{21} & 1 & \cdots & a_{2n} \\ 
\vdots & \vdots & \ddots & \vdots \\ 
a_{n1} & a_{n2} & \cdots & 1 
\end{pmatrix}$$
Com a propriedade de reciprocidade: $a_{ji} = \frac{1}{a_{ij}}$.

### 3. Extração dos Pesos ($w$)
O vetor de pesos $w$ corresponde ao autovetor principal normalizado da matriz de comparações:
$$A w = \lambda_{\max} w$$
Onde $\lambda_{\max}$ é o maior autovalor da matriz $A$. O resolvedor do SAD calcula essa aproximação normalizando as colunas da matriz e tirando a média aritmética das linhas correspondentes:
1. Normalização das colunas: $a'_{ij} = \frac{a_{ij}}{\sum_{k=1}^n a_{kj}}$
2. Vetor de pesos: $w_i = \frac{1}{n} \sum_{j=1}^n a'_{ij}$

### 4. Razão de Consistência ($CR$)
Para garantir a lógica dos julgamentos do decisor (ex: se $C_1 > C_2$ e $C_2 > C_3$, então $C_1$ deve ser muito maior que $C_3$), calcula-se a consistência:
1. O Índice de Consistência ($CI$) é calculado por:
   $$CI = \frac{\lambda_{\max} - n}{n - 1}$$
   Onde $\lambda_{\max} = \frac{1}{n} \sum_{i=1}^n \frac{(Aw)_i}{w_i}$.
2. A Razão de Consistência ($CR$) é calculada comparando $CI$ com um Índice de Consistência Aleatório ($RI$):
   $$CR = \frac{CI}{RI}$$

Onde $RI$ é tabelado de acordo com a dimensão $n$:
| $n$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|----|
| $RI$ | 0.00 | 0.00 | 0.58 | 0.90 | 1.12 | 1.24 | 1.32 | 1.41 | 1.45 | 1.49 |

* **Critério de Validade:** Se $CR < 0.10$ (10%), os julgamentos são considerados consistentes e válidos. Se $CR \ge 0.10$, o decisor deve revisar suas avaliações.

---

## 🚀 Instalação e Execução
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
Acesse: `http://127.0.0.1:5000`
