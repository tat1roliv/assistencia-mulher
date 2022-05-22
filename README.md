O aplicativo desenvolvido apresenta um design usável e intuitivo, de fácil compreensão para qualquer pessoa, observando-se os processos e boas práticas de UX e UI, com a prototipação realizada no Figma.
A aplicação contempla uma Landing Page-LP contendo um formulário, que apresenta uma tela de resultado, com um dado dinâmico, construído a depender dos combinação de dados fornecidas pelo usuário, , apontado se o usuário sofre algum tipo de violência ou não. 
O front-end da aplicação foi construído em HTML5 e estilizado com o CSS3 e a biblioteca Bootstrap em sua versão 4.0, carregada localmente, além integrações realizadas com JavaScript e NodeJs. 
As páginas da aplicação, a LP [ index.html ] e a página de resposta [ resposta.html ] foram desenvolvidas para o formato Web, além de adaptar-se a resoluções para tablet e mobile, utilizando tanto recursos estruturais da biblioteca Bootstrap quanto media queries, comportando as resoluções que vão desde 1920px de largura até 375px e com layouts intermediários específicos para 576px e 768px.
O formulário da LP é construído dinamicamente por JavaScript, através do arquivo [ main.js ], que gera pares de input e checkbox para cada pergunta do questionário, obtidos através do banco de dados, por meio de uma requisição do tipo GET na URI '/'
A página [ resposta.html ] é construída com elementos estáticos, com informações comuns à todas as respostas possíveis, com um único dado dinâmico. O dado é obtido por JavaScript [ resposta.js ], que no caso de ter resposta positiva para algum tipo de violência, captura o(s) parâmetro(s) correspondentes e insere dinamicamente na tela de resposta.
O back-end é uma API contruída com nodejs, express e o banco de dados MySQL. O projeto usou a arquitetura MVC para organizar o código e facilitar o crescimento da aplicação no futuro.
A API expoe dois endpoints para sua utilização [ server/routers/formularioRouter.js ], o endpoints '/' do tipo GET que busca no banco de dados todo o conteúdo da tabela perguntas e devolve um array de objetos contendo uma lista de perguntas para que o formulário possa ser renderizado, e o endpoint '/resposta' do tipo POST que recebe a resposta que foram marcadas no formulário pelo usuário, gera as violências sofridas pelo o usuário do sistemas, salva essas violências no banco de dados e posteriormente devolve as violencias sofridas para o usuário como uma string.
Na construção da API houve a preocupação em se separar as configurações do banco de dados do código por meio do módulo 'config', que utiliza o arquivo 'config/default.json' para armazer suas configurações.
Ainda houve o tratamento de erros de forma que tando o desenvolvedor localizará rapidamente os erros, quanto o usuário será avisado também por meio do status code do protocolo HTTP e também de uma mensagem de fácil compreenção.