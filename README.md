# Extração de Dados da Cartilha em PDF

Este repositório tem como objetivo apresentar uma solução desenvolvida por mim para uma fase piloto de um [projeto de pesquisa](http://cepats.unb.br/projetos/em-andamento/2-publicacoes/59-mmdh).
![fluxo geral](https://user-images.githubusercontent.com/97196457/214863818-608dc989-14ae-449b-8965-b29e19d21840.png)

# 1. Problema de Negócio
Com o objetivo de mapear as redes estaduais e locais de enfrentamento à violência contra as mulheres, em uma fase piloto, precisaríamos levantar essas redes para o Distrito Federal.
# 2. Resultados Obtidos
Foi encontrado a cartilha da redes de proteção à mulher feita, em 2021, pelo Tribunal de Justiça do Distrito Federal e dos Territórios. Com isso, aproveitamos esse trabalho, extraímos os dados do arquivo pdf fornecido e criamos um dashboard.

## 2.1. Menu
![image](https://user-images.githubusercontent.com/97196457/214965121-87c45a69-9fb2-4e35-a6c7-1b2ba5ac4775.png)
## 2.2 Consulta das Redes
![consulta redesss](https://user-images.githubusercontent.com/97196457/216055615-269209ce-acc0-40c8-bd05-7c30eae47328.png)
## 2.3 Análise das Redes
![analise redesss](https://user-images.githubusercontent.com/97196457/216055631-70fdce76-3b7d-4ea3-b0a5-ec2f13689183.png)

# 3. Processo Desenvolvido

1. Analise do arquivo pdf (formato das informações, campos possíveis, padrões e possíveis dificuldades).
2. Criação e extração das informações do pdf por meio de um [script Python](https://github.com/renankalfa/pdf-text-extract/blob/main/PDF_extract.ipynb).

    - Função destaque: por meio de um trecho de texto que se refere a uma instituição, ela trata e retorna um dicionário formatado da melhor forma.

```python
def get_dic_v2(t1):
    categorias = ['Endereço', 'Telefones Gerais', 'Fax', 'E-mail', 'Observações', 
                  'Observação', 'Atendimento', 'Horário', 'Público', 'Bens e Serviços',
                  'Bens e serviços', 'Critérios', 'Critério']
    l = []

    # Busca os índices de todos os tipos de informações
    for c in categorias:
        if c == 'Atendimento':
            l.append(t1.find(c, 30))
        else:
            l.append(t1.find(c))

    # Dicionário apenas com os tipos de informações presentes
    dic_contem = {}
    for c in range(len(l)):
        if l[c] != -1:
            dic_contem[categorias[c]] = l[c]
    dic_contem = dict(sorted(dic_contem.items(), key=lambda item: item[1]))

    # Coleta as informações de cada tipo de informações e transforma em um dicionário
    cont, dic_final= 0, {}
    nome, indice = '', 0
    for key, value in dic_contem.items():
        if cont != 0:
            dic_final[nome] = [t1[indice + len(nome):value]]
        else:
            dic_final['Instituição'] = [t1[:value]]
            indice = value
        cont = 1
        nome = key
        indice = value
    dic_final[nome] = [t1[indice + len(nome):]]
    return dic_final
```

3. Criação do dashboard por meio do Power BI.

# 4. Próximos Passos

1. Implementações de melhorias na limpeza do texto extraído do pdf.
2. Implementações de melhorias no campo "endereço".

# 5. Ferramentas Utilizadas

- Python (3.9.6)
- Jupyter Notebook (6.4.8)
- Power BI (2.111)
- Bibliotecas Python
  - Pandas (1.5.3)
  - PyPDF2 (3.1.0)

#

<a href="#top">Back to top</a>
