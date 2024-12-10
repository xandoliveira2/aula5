
# Projeto de Exemplo: Calculadora em Python

Este é um projeto simples de calculadora em Python usado para demonstrar como configurar CI/CD com Travis CI e GitHub Actions.

## Funcionalidades
- Soma
- Subtração
- Multiplicação
- Divisão (com verificação de divisão por zero)

---

## Pré-requisitos
- Python 3.8 ou superior
- Git

---

## Passo a Passo

### 1. Clonar o Repositório
```bash
git clone <https://github.com/pedroAmalfi/FatecItapira.git>
cd <FATECITAPIRA>
```

### 2. Configurar o Ambiente
Crie um ambiente virtual e instale as dependências:
```bash
python -m venv venv
source venv/bin/activate # Para Linux/Mac
venv\Scripts\activate  # Para Windows
pip install -r requirements.txt
```

### 3. Executar os Testes Localmente
Verifique se os testes estão funcionando:
```bash
python -m unittest test_calculadora.py
```

---

## Configurando CI/CD

### Travis CI
1. Acesse [Travis CI](https://travis-ci.com/) e conecte seu repositório.
2. Crie o arquivo `.travis.yml` no repositório com o seguinte conteúdo:
```yaml
language: python
python:
  - "3.8"
install:
  - pip install -r requirements.txt
script:
  - python -m unittest test_calculadora.py
```
3. Faça um commit e um push para iniciar o build.

### GitHub Actions
1. No GitHub, vá até a aba **Actions** do seu repositório.
2. Crie um arquivo no caminho `.github/workflows/python-app.yml` com o seguinte conteúdo:
```yaml
name: Python application

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.8'
    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt
    - name: Run tests
      run: |
        python -m unittest test_calculadora.py
```
3. Faça um commit e um push para iniciar o workflow.

---

## Resultados
- Testes automatizados executados a cada push ou pull request no repositório.
- Feedback imediato sobre erros ou falhas no código.

---
