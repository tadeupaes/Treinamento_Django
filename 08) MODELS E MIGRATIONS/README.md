# MODELS E MIGRATIONS

Os modelos (models) e as migrações são componentes essenciais em um projeto Django. Os modelos são responsáveis por definir a estrutura dos dados que serão armazenados no banco de dados, enquanto as migrações são usadas para criar ou modificar a estrutura do banco de dados de acordo com as definições dos modelos. Vou explicar como criar modelos e executar migrações em um projeto Django:

**1. Criando Modelos:**

Os modelos são criados em um aplicativo Django no arquivo `models.py`. Cada modelo representa uma tabela no banco de dados e define os campos e relacionamentos dessa tabela. Aqui está um exemplo simples de um modelo que representa uma lista de tarefas:

```python
from django.db import models

class Tarefa(models.Model):
    titulo = models.CharField(max_length=200)
    descricao = models.TextField()
    concluida = models.BooleanField(default=False)

    def __str__(self):
        return self.titulo
```

Neste exemplo, criamos um modelo `Tarefa` com três campos: `titulo`, `descricao` e `concluida`. O campo `titulo` é uma string de no máximo 200 caracteres, `descricao` é um campo de texto e `concluida` é um campo booleano que indica se a tarefa está concluída ou não.

**2. Criando Migrações:**

Após definir os modelos, é necessário criar migrações para que o Django crie as tabelas correspondentes no banco de dados ou faça alterações na estrutura do banco de dados. Para criar migrações, use o seguinte comando:

```bash
python manage.py makemigrations
```

Isso examinará os modelos definidos em seu aplicativo e gerará um arquivo de migração no diretório `migrations` do seu aplicativo. O arquivo de migração contém instruções para criar ou modificar as tabelas do banco de dados.

**3. Aplicando Migrações:**

Após criar as migrações, você deve aplicá-las ao banco de dados com o seguinte comando:

```bash
python manage.py migrate
```

Isso executará as migrações pendentes e criará ou modificará as tabelas no banco de dados de acordo com os modelos definidos.

**4. Usando o Admin do Django:**

Uma maneira conveniente de interagir com os modelos e os dados no banco de dados é através do sistema de administração do Django. Para isso, você precisa registrar os modelos no arquivo `admin.py` do seu aplicativo. Por exemplo:

```python
from django.contrib import admin
from .models import Tarefa

admin.site.register(Tarefa)
```

Depois de registrar um modelo, você pode acessar o sistema de administração em `http://127.0.0.1:8000/admin/` (seu servidor de desenvolvimento deve estar em execução) e gerenciar os dados do modelo, incluindo adicionar, editar e excluir registros.

**5. Trabalhando com Dados:**

Agora que você tem modelos e migrações configurados, pode criar, recuperar, atualizar e excluir dados do banco de dados usando o Django. Por exemplo, para criar uma nova tarefa:

```python
nova_tarefa = Tarefa(titulo="Minha nova tarefa", descricao="Descrição da tarefa", concluida=False)
nova_tarefa.save()
```

Para recuperar todas as tarefas não concluídas:

```python
tarefas_nao_concluidas = Tarefa.objects.filter(concluida=False)
```

Essas são as etapas básicas para criar modelos e executar migrações em um projeto Django. À medida que você desenvolve seu aplicativo, pode criar modelos adicionais e executar migrações conforme necessário para refletir as mudanças na estrutura de dados. O Django facilita a interação com bancos de dados e a criação de aplicativos com funcionalidades de banco de dados robustas.

**2º Exemplo**    
Vamos dar sequencia a um outra exemplos, analisando o cenario abaixo para o desenvolvimento do Model 

**EmpresaTI:** Representa a empresa de tecnologia.

**Desenvolvedor:** Representa os desenvolvedores que trabalham na empresa.

**Projeto:** Representa os projetos, que têm uma relação ManyToMany com os desenvolvedores e uma ForeignKey com a empresa.

**Modelos:**
EmpresaTI: Representa a empresa de tecnologia.

Desenvolvedor: Representa os desenvolvedores que trabalham na empresa.

Projeto: Representa os projetos, que têm uma relação ManyToMany com os desenvolvedores e uma ForeignKey com a empresa.

Criando Modelo Empresa para um campo nome 

```python
from django.db import models

class EmpresaTI(models.Model):
    nome = models.CharField(max_length=100)

    def __str__(self):
        return self.nome
```
**Campos:**
nome: Campo de texto (CharField) que armazena o nome da empresa. O tamanho máximo permitido é 100 caracteres.
**Métodos:**
__str__: Método especial que retorna o nome da empresa quando a instância é convertida em string, facilitando a leitura dos dados.

**Vamos analisar uma consultar via shell**

Via terminal carregamos o modulo Shell - Abra o Shell do Django

```Terminal ou CMD  - Abra o Shell do Django

python manage.py shell

```
Logo apos carregamos o model no shell - Importe o Modelo

Seguindo a seguinte sintaxe

```Sintaxe

from nome_aplicacao.models import nome_model  <enter>

```
Nosso exemplo que nosso model esta numa aplicação chamado appexemplo e carregamos nosso model EmpresaTI
```Python

from appexemplo.models import EmpresaTI  <enter>

```

**Inserindo dados no Model**

Para inserir dados no modelo EmpresaTI, você precisará seguir alguns passos básicos. Primeiro, certifique-se de que seu ambiente de desenvolvimento Django esteja configurado e que você tenha criado e aplicado as migrações para seus modelos.

**Passos para Inserir Dados:**
1-Abra o Shell do Django: O shell interativo do Django permite que você trabalhe diretamente com seus modelos.

2-Importe o Modelo: Importe o modelo EmpresaTI no shell.

3-Crie e Salve Instâncias: Crie instâncias do modelo e salve-as no banco de dados.

**Crie e Salve Instâncias:**

Crie novas instâncias do modelo EmpresaTI e salve-as no banco de dados:

``` Python - # Criação de uma nova empresa
empresa1 = EmpresaTI(nome="Tech Innovators")
empresa1.save()
```

```Python - # Criação de outra empresa
empresa2 = EmpresaTI(nome="Future Solutions")
empresa2.save()
```

**Verifique os Dados Inseridos:**

Para verificar se os dados foram inseridos corretamente, você pode consultar o banco de dados:

```Python - # 01 - Recuperar todas as empresas
empresas = EmpresaTI.objects.all()

print(empresas) ou empresas
```

```Python - # 02 - Recuperar todas as empresas
empresas = EmpresaTI.objects.all()

empresas
```


Usando o For
```Python - # 03 - Recuperar todas as empresas
# Recuperar todas as empresas
empresas = EmpresaTI.objects.all()
for empresa in empresas:
    print(empresa.nome)
```

**CRIANDO MAIS MODEL E SEUS RELACIONAMENTOS E MELHORANDO OS FILTROS**

Vamos analisar o seguint cenario para uso e explicação de cada campo : 


**Nosso primeiro Class Model  - Empresa Ti**

EmpresaTI:

nome: Campo de texto para o nome da empresa de tecnologia.

```Python

class EmpresaTI(models.Model):
    nome = models.CharField(max_length=100)

    def __str__(self):
        return self.nome


```


**Segundo Class Model Linguaguem**

Linguagem:

nome: Campo de texto para o nome da linguagem de programação.

```Python
class Linguagem(models.Model):
    nome = models.CharField(max_length=50)

    def __str__(self):
        return self.nome

```

**Terceiro Class Model Desenvolvedor:**

Desenvolvedor:

nome: Campo de texto para o nome do desenvolvedor.

empresa: Chave estrangeira para a EmpresaTI, indicando a qual empresa o desenvolvedor pertence.

linguagens: Relação ManyToMany com Linguagem, indicando que um desenvolvedor pode dominar várias linguagens de programação.

```Python

class Desenvolvedor(models.Model):
    nome = models.CharField(max_length=100)
    empresa = models.ForeignKey(EmpresaTI, on_delete=models.CASCADE)
    linguagens = models.ManyToManyField('Linguagem')

    def __str__(self):
        return self.nome

```

**Quarto Class Model Projeto:**

Projeto:

titulo: Campo de texto para o título do projeto.
empresa: Chave estrangeira para a EmpresaTI, indicando a qual empresa o projeto pertence.
desenvolvedores: Relação ManyToMany com Desenvolvedor, indicando que um projeto pode ter vários desenvolvedores e um desenvolvedor pode participar de vários projetos.

```Python

class Projeto(models.Model):
    titulo = models.CharField(max_length=200)
    empresa = models.ForeignKey(EmpresaTI, on_delete=models.CASCADE)
    desenvolvedores = models.ManyToManyField(Desenvolvedor)

    def __str__(self):
        return self.titulo

```


**Explicando as relações**

EmpresaTI: Uma empresa pode ter muitos desenvolvedores e muitos projetos.
Desenvolvedor: Um desenvolvedor trabalha para uma empresa e pode conhecer várias linguagens de programação.
Linguagem: Uma linguagem pode ser conhecida por muitos desenvolvedores.
Projeto: Um projeto é realizado por uma empresa e pode envolver vários desenvolvedores.

Essa modelagem permite uma flexibilidade significativa ao lidar com as relações complexas entre empresas, desenvolvedores, linguagens de programação e projetos em um ambiente de desenvolvimento de software.


