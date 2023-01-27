# Extração de Dados da Cartilha em PDF

Este repositório tem como objetivo apresentar uma solução desenvolvida por mim para uma fase piloto de um [projeto de pesquisa](http://cepats.unb.br/projetos/em-andamento/2-publicacoes/59-mmdh).
![fluxo geral](https://user-images.githubusercontent.com/97196457/214863818-608dc989-14ae-449b-8965-b29e19d21840.png)

# 1. Problema de Negócio
Com o objetivo de mapear as redes estaduais e locais de enfrentamento à violência contra as mulheres, em uma fase piloto, precisaríamos levantar essas redes para o Distrito Federal.
# 2. Resultados Obtidos
Foi encontrado a cartilha da redes de proteção à mulher feita, em 2021, pelo Tribunal de Justiça do Distrito Federal e dos Territórios. Com isso, aproveitamos esse trabalho, extraímos os dados do arquivo pdf fornecido e criamos um dashboard.

![image](https://user-images.githubusercontent.com/97196457/214965121-87c45a69-9fb2-4e35-a6c7-1b2ba5ac4775.png)

# 3. Processo Desenvolvido

1. Analise do arquivo pdf (formato das informações, campos possíveis, padrões e possíveis dificuldades).
2. Criação e extração das informações do pdf por meio de um [script Python](https://github.com/renankalfa/pdf-text-extract/blob/main/PDF_extract.ipynb).
3. Criação do dashboard por meio do Power BI.

# 4. Próximos Passos

1. Implementações de melhorias na limpeza do texto extraído do pdf.
2. Implementações de melhorias no campo "endereço".

# 5. Ferramentas Utilizadas

- Python (3.9.6)
- Jupyter Notebook (6.4.8)
- Power BI (2.111)
