# 📈 Operações de Taxa — Scanner

Dashboard para análise e visualização de oportunidades de operações de taxa (venda coberta de CALL e Collar) geradas pelo workflow n8n.

## 🚀 Como usar

### 1. Hospedar no GitHub Pages

```bash
# Clone ou crie um repositório
git init
git add .
git commit -m "feat: scanner operações de taxa"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/SEU_REPO.git
git push -u origin main
```

Ative o GitHub Pages em: **Settings → Pages → Source: main branch / root**

Acesse em: `https://SEU_USUARIO.github.io/SEU_REPO`

---

### 2. Configurar o n8n para enviar dados ao site

No workflow n8n, após o node **Agregar resultados**, adicione um node **HTTP Request** para salvar o JSON num Gist do GitHub ou num endpoint compatível com GitHub Pages.

**Alternativa simples:** copie o JSON do output do node `Agregar resultados` e cole diretamente no campo de entrada do site.

---

## ⚙️ Funcionalidades

| Feature | Descrição |
|---|---|
| 💰 Configuração de Caixa | Define valor disponível e % a alocar em operações |
| 📊 Barra de Alocação | Visualização da distribuição do caixa |
| 🎯 Cards de Oportunidade | Call Pura e Collar com todos os dados relevantes |
| 📈 Simulação de Ganho | Ganho estimado com 100, 1.000 e qtd sugerida pelo caixa |
| 🤖 Análise com IA | Claude analisa as oportunidades e recomenda a melhor estratégia |
| 🧪 Demo | Dados fictícios para testar sem precisar do n8n |

---

## 🤖 Análise com IA

A análise usa a API da Anthropic (Claude). Para usar:
1. Gere sua API Key em [console.anthropic.com](https://console.anthropic.com)
2. Cole-a no campo **Anthropic API Key** na configuração
3. Clique em **✨ Analisar com IA**

A IA avalia:
- Taxa líquida vs CDI
- Volatilidade implícita (distância do strike)
- Liquidez e book de ofertas
- Risco de exercício antecipado (opções americanas)
- Relação risco/retorno CALL pura vs Collar

---

## 📋 Formato do JSON esperado

Cole o output do node **Agregar resultados** do n8n:

```json
{
  "resultados": [
    {
      "cdi_dia": 0.054266,
      "cdi_mes": 1.15,
      "ipca_ano": 4.14,
      "puras": [ ...array de calls puras... ],
      "collars": [ ...array de collars... ]
    }
  ]
}
```

---

## ⚠️ Aviso Legal

Análise informativa. Não constitui recomendação de investimento. Consulte um profissional habilitado antes de tomar decisões financeiras.
