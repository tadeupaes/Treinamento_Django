Baseado num fork fiz algumas correções,modificações e implementações

# INICIANDO NO MUNDO DJANGO - INTRODUÇÃO, INSTALAÇÃO E CONFIGURAÇÃO

## Introdução ao Django:
Django é conhecido por seguir o princípio "batteries-included", o que significa que ele fornece uma série de funcionalidades prontas para uso, como autenticação de usuário, sistema de administração, ORM (Object-Relational Mapping), e muito mais. Ele segue o padrão de projeto Model-View-Template (MVT) e é projetado para promover um código limpo, reutilizável e organizado.


##Criando um Projeto Django em um Ambiente Virtual Python (venv)

Usar um ambiente virtual (venv) para projetos Django é uma prática recomendada, pois ele isola as dependências do projeto e evita conflitos entre diferentes projetos. Aqui estão as etapas detalhadas para configurar um projeto Django em um ambiente virtual.

Passos:
01-Instalar Python e pip: Certifique-se de que Python e pip (gerenciador de pacotes do Python) estejam instalados no seu sistema.

```Python
python --version
pip --version
```

02-Criar um Ambiente Virtual: Use venv para criar um ambiente virtual, onde vprojeto nome do seu ambiente. Nas questões relacionandas a django não confunda o projeto do django com ambiente virtual criado 

```Python
python -m venv ambiente
```

03-Ativar o Ambiente Virtual:

```WIndows

ambiente\Scripts\activate

```

```Macos e Linux

source myenv/bin/activate

```
Nesse momento podera ir para processo de instalação do django.


## Instalação do Django:
Para começar a usar o Django, siga estas etapas para instalar o framework:

1. **Pré-requisitos:**
   - Certifique-se de que você tenha o Python instalado. O Django é compatível com Python 3.6 ou superior.

2. **Instalação do Django:**
   - Abra um terminal ou prompt de comando e use o gerenciador de pacotes `pip` para instalar o Django:

   ```bash
   pip install django
   ```

   Isso instalará a versão mais recente do Django em seu ambiente Python.

## Configuração Inicial do Django:
Depois de instalar o Django, você pode criar um projeto e configurá-lo da seguinte forma:

1. **Criar um Projeto:**
   - Para criar um projeto Django, use o seguinte comando no terminal:

   ```bash
   django-admin startproject nome_do_projeto
   ```

   Substitua `nome_do_projeto` pelo nome do seu projeto.

2. **Executar o Servidor de Desenvolvimento:**
   - Navegue para o diretório do projeto que você acabou de criar:

   ```bash
   cd nome_do_projeto
   ```

   - Inicie o servidor de desenvolvimento com o seguinte comando:

   ```bash
   python manage.py runserver
   ```

   Isso iniciará o servidor local em `http://127.0.0.1:8000/`.

   Caso queria direcionar uma porta logo apos runserver direcione para uma porta desejada

4. **Acessar a Página Inicial do Admin (opcional):**
   - O Django inclui um sistema de administração. Para usá-lo, crie um superusuário com o seguinte comando:

   ```bash
   ptyhon manage.py migrate
   python manage.py createsuperuser
   ```

   Siga as instruções para criar um superusuário, que pode ser usado para acessar a interface de administração em `http://127.0.0.1:8000/admin/`.

Agora você tem o Django instalado, um projeto criado e o servidor de desenvolvimento em execução. Você está pronto para começar a desenvolver seu aplicativo web Django.

Lembre-se de que esta é apenas uma configuração inicial. Conforme você avança no desenvolvimento do seu projeto, você definirá modelos, views, URLs e templates de acordo com as necessidades específicas do seu aplicativo.
