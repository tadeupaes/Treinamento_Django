
# Django ORM - Conceito e Exemplos

Este documento fornece uma visão geral do ORM (Object-Relational Mapping) do Django, juntamente com exemplos práticos para ilustrar seu uso.

## Conceito

O Django ORM é uma camada de abstração que permite interagir com o banco de dados usando objetos Python, em vez de escrever consultas SQL diretamente. Ele facilita a manipulação de dados do banco de dados através de classes e métodos Python, tornando o código mais legível e fácil de manter.

## Definição de Modelos

Vamos definir um modelo `Empresa` com alguns campos básicos.

```python
from django.db import models

class Empresa(models.Model):
    nome = models.CharField(max_length=100)
    endereco = models.CharField(max_length=255)
    data_fundacao = models.DateField()

    def __str__(self):
        return self.nome
```

## Criação de Objetos

Criação de um novo registro no banco de dados.

```python
# Usando o shell do Django
$ python manage.py shell

>>> from app.models import Empresa
>>> nova_empresa = Empresa(nome="Tech Corp", endereco="Rua das Flores, 123", data_fundacao="2020-01-01")
>>> nova_empresa.save()
```

## Leitura de Objetos

Consultando registros no banco de dados.

```python
>>> todas_empresas = Empresa.objects.all()
>>> for empresa in todas_empresas:
...     print(empresa.nome, empresa.endereco)
...

>>> empresa_especifica = Empresa.objects.get(id=1)
>>> print(empresa_especifica.nome, empresa_especifica.endereco)
```

## Atualização de Objetos

Atualizando um registro existente.

```python
>>> empresa_para_atualizar = Empresa.objects.get(id=1)
>>> empresa_para_atualizar.endereco = "Avenida Central, 456"
>>> empresa_para_atualizar.save()
```

## Exclusão de Objetos

Excluindo um registro do banco de dados.

```python
>>> empresa_para_excluir = Empresa.objects.get(id=1)
>>> empresa_para_excluir.delete()
```

## Consultas Avançadas

Utilizando filtros e consultas avançadas.

```python
# Filtrar empresas fundadas após 2010
>>> empresas_recentes = Empresa.objects.filter(data_fundacao__gte="2010-01-01")
>>> for empresa in empresas_recentes:
...     print(empresa.nome, empresa.data_fundacao)
...

# Ordenar empresas por nome
>>> empresas_ordenadas = Empresa.objects.all().order_by('nome')
>>> for empresa in empresas_ordenadas:
...     print(empresa.nome)
...
```
