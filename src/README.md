# Código da Aplicação

Esta pasta contém o código do seu agente financeiro.

```python
import json
import panda as pd

perfil = json.load('./data/perfil_investidor.json')
produtos = json.load('./data/produtos_financeiros.json')
transacoes = pd.read_csv('./data/transacoes.csv')
historico = pd.read_csv('./data/historico_atendimento.csv')

contexo = f"""
CLIENTE: {perfil['nome']}, {perfil['idade']} anos, perfil {perfil['perfil_investidor']}
OBJETIVO: {perfil['perfil_principal']}
PATRIMONIO: R$ {perfil['patrimonio_total']}, RESERVA: R$ {perfil['reserva_emergencial_atual']}

TRANSACOES RECENTES: 
{transacoes.to_string(index=false)}

ATENDIMENTOS ANTERIORES:
{historico.to_string(index=false)}

PRODUTOS DISPONIVEIS:
{json.dumps(produtos, ident=2, ensure_ascii=false)}
"""

SYSTEM_PROMPT = """Profi, professor financeiro

OBJETIVO
Ensinar conceito financeiro de forma simples.

REGRAS:
1. Sempre baseie suas respostas nos dados fornecidos
2. Nunca invente informações financeiras
3. Se não souber algo, admita e ofereça alternativas
"""
```

## Estrutura Sugerida

```
src/
├── app.py              # Aplicação principal (Streamlit/Gradio)
├── agente.py           # Lógica do agente
├── config.py           # Configurações (API keys, etc.)
└── requirements.txt    # Dependências
```

## Exemplo de requirements.txt

```
streamlit
openai
python-dotenv
```

## Como Rodar

```bash
# Instalar dependências
pip install -r requirements.txt

# Rodar a aplicação
streamlit run app.py
```
