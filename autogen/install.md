## Instalar AutoGen no Linux

#### 1. Certifique-se de ter o Python3 instalado
> python3 --version

#### 2. Instale o pip
> sudo apt install python3-pip -y

#### 3. Instale o ambiente virtual Python .venv
> sudo apt install python3-venv -y

#### 4. Ative o ambiente virtual
> python3 -m venv .venv
> source .venv/bin/activate

#### 5. Instale o AutoGen
> pip install autogen-agentchat~=0.2
