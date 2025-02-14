# Extração Dados

1 - Define dados fictícios de funcionários extraídos de um banco SQL.
2 - Extrai os nomes das colunas a partir da descrição dos dados.
3 - Cria um DataFrame Pandas para organizar os dados em formato tabular.
4 - Exibe a tabela (dependendo do ambiente).
5 - Gera um texto com a lista de funcionários e seus cargos, para envio ao RH.

1️⃣ Definição de dados:
  - O script simula a extração de informações de um banco de dados SQL e armazena os dados manualmente na variável *informacoes*.
  - *informacoes* contém uma lista de tuplas, onde cada tupla representa um funcionário com os seguintes detalhes:
      * ID, Nome, Cargo, Salário Base, Hora Extra, Outros Pagamentos, Benefícios, Total Recebido, Total com Benefícios, Ano, Notas, Agência, Status.
  - A variável *descricao* contém a estrutura das colunas da tabela, com nome, tipo de dado e algumas propriedades.

2️⃣ Criação de uma lista com os nomes das colunas
  - O script extrai os nomes das colunas a partir da variável descricao, pegando o primeiro elemento de cada tupla:
          colunas = [tupla[0] for tupla in descricao]
          
  - Isso resulta em uma lista de nomes de colunas, como ["Id", "EmployeeName", "JobTitle", "BasePay", ...]

3️⃣ Criação de um DataFrame Pandas
    - O script cria uma tabela (*DataFrame*) usando *pandas*, com os dados da lista *informacoes* e atribui os nomes de colunas da lista *colunas*:
        tabela = pd.DataFrame.from_records(informacoes, columns=colunas)

4️⃣ Exibição da Tabela
   - Se estiver rodando em um Jupyter Notebook, o comando display(tabela) exibe a tabela formatada.
   - Se rodar no terminal, o ideal seria substituir por print(tabela).

5️⃣ Construção do texto do e-mail
  - O script monta um texto para enviar ao RH, listando os funcionários e seus cargos.
  - Inicializa a variável texto com a introdução:
      texto = "RH, segue a lista dos funcionários"
    
  - Percorre a lista *informacoes* e adiciona cada funcionário ao texto:
      for tupla in informacoes:
        nome_funcionario = tupla[1]
        cargo = tupla[2]
        texto = texto + f"\n{nome_funcionario}, Cargo: {cargo}"

    Por fim, imprime o texto formatado.

