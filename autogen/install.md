# **Configuração do Ambiente Virtual (venv) e VSCode para AutoGen**

Este guia descreve os passos necessários para configurar um ambiente Python com **AutoGen** em um ambiente virtual, além da integração com o **VSCode**.

---

## **1. Criação do Ambiente Virtual**

1. **Abra o terminal** e vá até a pasta do seu projeto:
   ```bash
   cd ~/caminho/para/seu_projeto
   ```

2. **Crie um ambiente virtual** chamado `.venv`:
   ```bash
   python3 -m venv .venv
   ```

3. **Ative o ambiente virtual**:
   - No **Linux/Mac**:
     ```bash
     source .venv/bin/activate
     ```
   - No **Windows**:
     ```cmd
     .venv\Scripts\activate
     ```

4. **Confirme que o ambiente virtual está ativo**:
   - O terminal deve exibir o prefixo `(.venv)`.
   - Verifique o caminho do Python:
     ```bash
     which python
     ```
     Saída esperada (exemplo):
     ```
     /caminho/para/seu_projeto/.venv/bin/python
     ```

---

## **2. Instalação do AutoGen**

Com o ambiente virtual ativo, instale o **AutoGen** usando o pip:
```bash
pip install pyautogen
```

Verifique se a instalação foi bem-sucedida:
```bash
pip show pyautogen
```

Saída esperada:
```
Name: pyautogen
Version: X.X.X
Location: /caminho/para/seu_projeto/.venv/lib/python3.X/site-packages
```

---

## **3. Configuração do VSCode**

### **3.1. Abra o Projeto no VSCode**
- No terminal, abra o VSCode no diretório do projeto:
  ```bash
  code .
  ```

### **3.2. Configure o Interpretador Python**

1. Pressione **Ctrl+Shift+P** (ou **Cmd+Shift+P** no Mac) para abrir a paleta de comandos.
2. Digite e selecione **"Python: Select Interpreter"**.
3. Escolha o interpretador **Python** que pertence ao ambiente virtual (`.venv`).
   - Ele estará no caminho:
     ```
     ~/.venv/bin/python
     ```

> **Dica**: Caso não apareça, reinicie o VSCode ou clique em **"Enter interpreter path"** e navegue até `.venv/bin/python`.

### **3.3. Verificação**
Crie um arquivo `test.py` no diretório `src` com o seguinte conteúdo:
```python
from autogen import AssistantAgent

print("AutoGen instalado e funcionando!")
```

Abra o terminal integrado do VSCode e execute:
```bash
python src/test.py
```

Saída esperada:
```
AutoGen instalado e funcionando!
```

---

## **4. Executando Scripts no Ambiente Virtual**
Sempre ative o ambiente virtual antes de rodar os scripts:
```bash
source .venv/bin/activate
```

Para desativar o ambiente virtual:
```bash
deactivate
```

---

## **5. Dicas Adicionais**

- **Verificar pacotes instalados**:
  ```bash
  pip list
  ```
- **Atualizar o pip**:
  ```bash
  pip install --upgrade pip
  ```
- **Gerar um arquivo de dependências**:
  ```bash
  pip freeze > requirements.txt
  ```
- **Instalar pacotes a partir de um arquivo**:
  ```bash
  pip install -r requirements.txt
  ```

---

## **Resumo Final**
1. Criar e ativar o ambiente virtual.
2. Instalar o AutoGen usando `pip install pyautogen`.
3. Configurar o interpretador Python no VSCode.
4. Testar o AutoGen com um script simples.

Agora você está pronto para usar o AutoGen em seu projeto Python no **VSCode**! 🎉
