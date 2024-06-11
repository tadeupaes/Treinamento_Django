# MANUAL
## CRIANDO UM AMBIENTE VIRTUAL (OPCIONAL):
1. **Crie o ambiente virtual:**
   Você pode instalar o `virtualenv` usando o `pip`, que é o gerenciador de pacotes do Python.

   Para instalar o `virtualenv`, você pode executar o seguinte comando:

   ```
   pip install virtualenv
   ```

   Depois de instalar o `virtualenv`, você pode criar um novo ambiente virtual com o seguinte comando:

   ```
   virtualenv venv
   ```

   Se quiser, você pode substituir "venv" pelo nome que você deseja dar ao seu ambiente virtual (Não se esqueça de atualizar o `.gitignore`). Em seguida, você pode ativar o ambiente virtual com os seguintes comandos:

   - No Windows:

   ```
   venv\Scripts\activate
   ```

   - No Linux/Mac:

   ```
   source venv/bin/activate
   ```

   Uma vez ativado o ambiente virtual, você pode tentar instalar os pacotes necessários usando o `pip`, e eles serão instalados apenas no escopo do ambiente virtual, evitando possíveis conflitos com outros pacotes no seu sistema.

## INSTALAÇÃO:
1. **Instalar o Python:**
   - Vá para o site [oficial do Python](https://www.python.org/).
   - Clique no botão "Downloads" na parte superior da página.
   - Na página de downloads, você verá a versão mais recente do Python disponível para download. Selecione a versão que corresponde ao seu sistema operacional (Windows, macOS ou Linux).
   - Baixe o instalador executável (`.exe` para Windows) e execute-o.
   - Na primeira tela do instalador, marque a caixa "Add Python X.X to PATH" (onde "X.X" é a versão do Python que você está instalando). Isso adicionará o Python à sua variável de ambiente PATH, permitindo que você use o Python e o pip (gerenciador de pacotes do Python) a partir do terminal ou prompt de comando.
   - Clique em "Install Now" e siga as instruções na tela para concluir a instalação.

2. **Verificar a instalação do Python:**
   - Após a instalação, abra o terminal ou prompt de comando.
   - Digite `python --version` e pressione Enter. Isso deve exibir a versão do Python que você acabou de instalar. Se isso funcionar corretamente, o Python foi instalado com sucesso em seu sistema.

3. **Instalar o Django:**
   - Uma vez que o Python esteja instalado, você pode instalar o Django usando o pip, que é o gerenciador de pacotes do Python.
   - Abra o terminal ou prompt de comando.
   - Digite o seguinte comando e pressione Enter:

     ```bash
     pip install django
     ```
     
     ```bash
     pip install django-admin
     ```

   Isso instalará a versão mais recente do Django em seu sistema.

4. **Verificar a instalação do Django:**
   - Para verificar se o Django foi instalado corretamente, você pode digitar o seguinte comando e pressionar Enter:

     ```
     python -m django --version
     ```

   Isso deve exibir a versão do Django que você acabou de instalar. Se isso funcionar corretamente, o Django foi instalado com sucesso em seu sistema.

## CRIANDO O PROJETO:
1. **Criando um Projeto:**
   No Django, um projeto é a estrutura global do seu aplicativo web. Para criar um projeto, use o comando `django-admin`:

   ```bash
   django-admin startproject nome_do_projeto
   ```

   Isso criará um diretório com o nome do projeto contendo a estrutura inicial.

2. **Criando um Aplicativo:**
   Em Django, um projeto pode conter vários aplicativos. Cada aplicativo é uma parte independente do projeto. Para criar um aplicativo vá no diretório do seu projeto e use o seguinte comando:

   ```bash
   python manage.py startapp nome_do_aplicativo
   ```

3. **Subindo o servidor:**
   Para subir o servidor de desenvolvimento do Django, você pode usar o comando `runserver`. Aqui está como fazê-lo:

   1. Abra o terminal.
   2. Navegue até o diretório do seu projeto Django, onde está localizado o arquivo `manage.py`.
   3. Execute o comando a seguir:

   ```bash
   python manage.py runserver
   ```

   Isso iniciará o servidor de desenvolvimento do Django. Por padrão, ele será executado na porta 8000. Se você quiser especificar uma porta diferente, você pode fornecer o número da porta após o comando, por exemplo:

   ```bash
   python manage.py runserver 8080
   ```

   Isso iniciará o servidor na porta 8080.

   Após executar o comando, você verá mensagens no terminal indicando que o servidor está sendo iniciado. Assim que o servidor estiver pronto, você poderá acessar seu aplicativo Django no navegador digitando o endereço `http://localhost:8000` (ou a porta que você especificou) na barra de endereço.

## SOBRE O `.gitignore`:
   O arquivo `.gitignore` é usado para especificar quais arquivos e diretórios o Git deve ignorar ao rastrear alterações em um projeto. Aqui estão alguns padrões comuns que você pode incluir no seu arquivo `.gitignore` ao trabalhar com projetos Django:

   ```
   migrations
   .pyc
   __pycache__
   .sqlite3
   .env
   venv/
   env/
   local_settings.py  
   log/
   media/
   staticfiles/
   ```

   Esses são apenas exemplos e você pode personalizar o `.gitignore` conforme necessário para o seu projeto específico. Certifique-se de incluir quaisquer arquivos ou diretórios que não devem ser versionados pelo Git, como arquivos de banco de dados, arquivos de configuração locais, diretórios de ambiente virtual, etc.

   Após criar ou atualizar seu arquivo `.gitignore`, certifique-se de adicioná-lo ao seu repositório Git para garantir que as exclusões sejam aplicadas corretamente:

   ```bash
   git add .gitignore
   git commit -m "Adicionado arquivo .gitignore"
   git push
   ```

   Isso garantirá que o Git ignore os arquivos e diretórios especificados no `.gitignore` ao rastrear alterações no seu projeto.

## SOBRE OS REQUIREMENTOS:
1. **Criando o requirements.txt:**
    Para criar o `requirements.txt`, você pode executar o seguinte comando:
    ```
    pip freeze > requirements.txt
    ```

    O comando `pip freeze` é utilizado para listar todas as dependências instaladas no ambiente Python juntamente com suas versões. Por exemplo, ao executar `pip freeze`, você verá uma lista de pacotes instalados e suas versões, algo assim:

    ```
    Flask==2.0.1
    Werkzeug==2.0.2
    ...
    ```

    Já o símbolo `>` é usado para redirecionar a saída de um comando para um arquivo. No caso específico do `pip freeze`, o redirecionamento para um arquivo chamado `requirements.txt` é uma prática comum para criar um arquivo que liste todas as dependências do projeto.

    Portanto, quando você executa `pip freeze > requirements.txt`, está dizendo ao Python para listar todas as dependências e salvar essa lista no arquivo `requirements.txt`. Isso é útil para compartilhar o ambiente de desenvolvimento com outras pessoas ou para garantir que você possa instalar exatamente as mesmas versões das dependências em outro ambiente.

2. **Instalando as dependências:**
    Antes de executar o aplicativo, é essencial garantir que todas as dependências necessárias estejam instaladas. O arquivo `requirements.txt` contém uma lista das dependências e suas versões correspondentes. Para instalar essas dependências, siga estas etapas:

    1. Abra o terminal ou prompt de comando na pasta raiz do seu projeto.

    2. Execute o seguinte comando para instalar as dependências listadas no arquivo `requirements.txt`:
    
        ```bash
        pip install -r requirements.txt
        ```

    Isso instruirá o pip a ler o arquivo `requirements.txt` e instalar todas as dependências listadas, garantindo que o ambiente de desenvolvimento seja configurado corretamente.

    3. Aguarde até que todas as dependências sejam baixadas e instaladas. Isso pode levar alguns minutos, dependendo do número e do tamanho das dependências.

    4. Após a conclusão da instalação, você estará pronto para executar o aplicativo Flask sem problemas de dependências ausentes.

## EXEMPLOS DE CÓDIGOS:
1. **Modelos:**
   Os modelos no Django definem a estrutura do banco de dados. Aqui está um exemplo de um modelo para uma lista de tarefas:

   ```python
   from django.db import models

   class Tarefa(models.Model):
       titulo = models.CharField(max_length=200)
       concluida = models.BooleanField(default=False)

       def __str__(self):
           return self.titulo
   ```

2. **Administração:**
   O Django inclui um painel de administração que facilita a gestão dos dados do aplicativo. Para usar o admin, registre seus modelos no arquivo `admin.py` do seu aplicativo:

   ```python
   from django.contrib import admin
   from .models import Tarefa

   admin.site.register(Tarefa)
   ```

3. **Views e URLs:**
   As views processam solicitações do cliente e retornam respostas. Você define as URLs que correspondem a essas views no arquivo `urls.py`:

   ```python
   from django.urls import path
   from . import views

   urlpatterns = [
       path('tarefas/', views.lista_tarefas, name='lista_tarefas'),
   ]
   ```

4. **Controladores (Views):**
   As views controlam a lógica do aplicativo e renderizam os templates. Aqui está um exemplo de uma view que renderiza uma lista de tarefas:

   ```python
   from django.shortcuts import render
   from .models import Tarefa

   def lista_tarefas(request):
       tarefas = Tarefa.objects.all()
       return render(request, 'lista_tarefas.html', {'tarefas': tarefas})
   ```

5. **Templates HTML:**
    Você pode criar templates HTML para exibir os dados em suas páginas. Aqui está um exemplo simples:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>Lista de Tarefas</title>
    </head>
    <body>
        <h1>Minha Lista de Tarefas</h1>
        <ul>
            {% for tarefa in tarefas %}
                <li>{{ tarefa.titulo }}</li>
            {% endfor %}
        </ul>
    </body>
    </html>
    ```

## DIRETÓRIOS:
```
meu_projeto/                  # Diretório raiz do projeto
│
├── meu_app/                  # Diretório do aplicativo principal
│   ├── migrations/           # Diretório de migrações de banco de dados
│   ├── __init__.py           # Arquivo de inicialização do aplicativo
│   ├── admin.py              # Configurações de administração do Django
│   ├── apps.py               # Configurações do aplicativo
│   ├── models.py             # Definições de modelos do banco de dados
│   ├── tests.py              # Testes do aplicativo
│   └── views.py              # Views do aplicativo
│
├── meu_projeto/              # Diretório de configuração do projeto Django
│   ├── __init__.py           # Arquivo de inicialização do projeto
│   ├── asgi.py               # Configurações para ASGI (Servidor de Interface de Gateway Assíncrona)
│   ├── settings.py           # Configurações do projeto
│   ├── urls.py               # Configurações de URLs do projeto
│   └── wsgi.py               # Configurações para WSGI (Interface de Gateway da Web)
│
├── static/                    # Diretório para arquivos estáticos (CSS, JavaScript, imagens)
│
├── templates/                 # Diretório para arquivos de modelos (HTML)
│
├── media/                     # Diretório para arquivos de mídia (uploads de usuário, etc.)
│
├── manage.py                  # Script de gerenciamento do Django
│
└── .gitignore                 # Arquivo para especificar arquivos/diretórios a serem ignorados pelo Git
```

Esta é uma estrutura de diretórios típica para um projeto Django. Aqui está uma breve explicação de cada diretório e arquivo:

- `meu_app/`: Este diretório contém todos os componentes específicos do aplicativo, como modelos, visualizações, URLs, etc.
- `meu_projeto/`: Este diretório contém as configurações do projeto Django, incluindo configurações globais, URLs principais e scripts de inicialização.
- `static/`: Este diretório é usado para armazenar arquivos estáticos, como CSS, JavaScript e imagens.
- `templates/`: Este diretório é usado para armazenar arquivos de modelos HTML para renderização de páginas da web.
- `media/`: Este diretório é usado para armazenar arquivos de mídia, como uploads de usuário.
- `manage.py`: Este é o script de gerenciamento do Django usado para realizar várias tarefas, como executar o servidor de desenvolvimento, aplicar migrações de banco de dados, etc.
- `.gitignore`: Este arquivo especifica quais arquivos e diretórios devem ser ignorados pelo Git ao rastrear alterações no projeto.

Esta estrutura de diretórios é uma base comum para projetos Django, mas pode variar dependendo das necessidades específicas do projeto.

Baseado no Fork.