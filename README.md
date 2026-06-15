# Nexus AHP — Priorização Hierárquica Matricial

Este repositório é o módulo independente do ecossistema **NEXUS MCDM**, configurado para operar exclusivamente com o método **AHP (Analytic Hierarchy Process)**.

---

## 🎨 Identidade Visual e Branding
- **Nome Oficial:** Nexus AHP
- **Cores Oficiais:** Dourado (`#D97706`) e Grafite (`#4B5563`)
- **Conceito Visual:** Árvore hierárquica de decisão representando as ramificações de múltiplos níveis de critérios.
- **Copyright:** Direitos Reservados © 2026 NEXUS-MCDM.

---

## 🌟 Recursos e Matemática

- **Escala de Saaty:** Comparações par a par entre critérios na escala de 1 (igual importância) a 9 (importância extrema).
- **Consistência (CR):** O resolvedor calcula o vetor de pesos via autovetor principal e gera a Razão de Consistência (CR):
  - `CR = CI / RI`
  - Se `CR < 0.10` (10%), os julgamentos do decisor são considerados consistentes.
- **Relatório PDF & Excel TCC:** Exportação de relatório de resultados completo com auditoria matricial em PDF e importação de planilhas.

---

## 🚀 Instalação e Execução
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python app.py
```
