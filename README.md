# web-server-logs

> Este repositório possui um workflow utilizando notebook python, que é capaz de realizar um download de arquivo de log web server, ingerir em uma tabela delta e realizar apresentação de análises de dados.


1. Identificar as 10 maiores origens de acesso (Client IP) por quantidade de acessos.
2. Listar os 6 endpoints mais acessados, desconsiderando aqueles que representam arquivos
3. Quantidade de Client IPs distintos
4. Quantos dias de dados estão representados no arquivo
5. Com base no tamanho em bytes do conteúdo das respostas:
   - O volume total de dados retornado
   - O maior volume de dados em uma única resposta
   - O menor volume de dados em uma única resposta
   - O volume médio de dados retornado
6. Qual dia da semana com maior número de erros do tipo 'HTTP Client Error'

# Acesso ao Projeto
> Para acessar ao projeto, faça o login utilizando sua conta github: https://github.com/  
> Acesse ao projeto utilizando a url: https://github.com/victorganjos/web-server-logs  

Este projeto foi desenvolvido utilizando o databricks community, para executá-lo sigas os passos à seguir!

# Configuração do projeto
> Realize o download do projeto através do comando no seu terminal com git instalado:  
> git clone https://github.com/victorganjos/web-server-logs.git  
Se não possui o git instalado, siga a documentação: https://git-scm.com/book/pt-br/v2/Come%C3%A7ando-Instalando-o-Git  

Após realizar o clone do projeto, será necessário criar uma conta gratuíta no databricks community!

> Acesse ao link: https://www.databricks.com/try-databricks#account
> Crie a sua conta gratuíta e efetue o login!

> Caso já tenha conta, acesse o link e efetue o login!
> Acesse ao link: https://community.cloud.databricks.com/  


Agora siga os passos abaixo:
> 1. No menu lateral, haverá uma opção chamada 'Compute', clique nela.

> 2. Após entrar na aba Compute, clique em 'Create compute'
>   1. Preencha o campo de compute name
>   2. Selecione a runtime 15.4LTS
>   3. Clique em 'Create compute' no final da página.

> 3. Após a criação do seu cluster (Compute), clique em 'Workspace', no menu lateral.

> 4. Na aba 'Workspace', haverá um ícone de 3 pontos na vertical, clique nele e depois em import.

> 5. Realize a importação do arquivo src.dbc, que encontra-se no diretório onde foi efetuado o comando git clone, 
dentro de src.


# Executando o projeto

> Contendo o diretório main na home de seu workspace no databricks community:   
> Entre no diretório src e acesse o arquivo 'main_processor_notebook'.    

> Com o arquivo aberto, haverá um ícone no canto superior direito 'Connect'
> Selecione o cluster (Compute) que foi criado nos passos de configuração do projeto.
> Em seguida clique em 'Run All'

Todos os notebooks necessários para a execução serão acionados por este principal 
e os resultados obtidos mostrados em tela de acordo com as seções descritas no notebook.

> As seções contendo os resultados das análises estão descritas e enumeradas de acordo com os itens da solicitação.
> Você poderá encontrá-las a partir do texto 'Obtenção dos resultados - Inicie por aqui!'

> Para executar os testes unitários, basta retornar o para diretório main e abrir o diretório tests, executando cada
arquivo individualmente.


# Notas do autor
Desenvolver o challenge através do databricks community foi uma escolha considerando os aspectos:
 
 - Cloud environment já preparado, sem necessidade de montar o ambiente docker
 - Facilidade na configuração e execução do projeto
 - Performance em trabalhar com os dados no formato delta

Como pontos de melhorias, poderia realizar as configurações dos parametros de entrada através de um arquivo json ou yaml,
removendo a necessidade de trabalhar com a inserção de váriaveis hard code. Estudo e aplicação de outros modos de
ingestão dos arquivos e a utilização de um blob storage para considerar o melhor uso de uma tier específica para melhor
gerenciamento dos recursos.

A criação das tabelas 'tb_raw_access_log' e 'tb_trusted_access_log' particionadas pela data corrente do processamento 
deu-se visando a manutenção de cargas efetuadas, obtendo possibilidade de consultar especificamente um carregamento.
O particionamento poderia ser estudado para o nome ou versão do arquivo também, a depender das variações de 
nomenclaturas possíveis, não sendo a data um único modo possível.


obrigado!!
