# Sistema-de-Gerenciamento-de-Biblioteca

Projeto desenvolvido por:
Robson Martins
MBA em Desenvolvimento de Aplicações Java - SOA / FIAP
24/06/2011

Tecnologias empregadas:
JPA e Hibernate;
Banco de Dados MySQL;
Generics;
DAO Patterns;
UI em modo console
 

Banco de Dados MySQL:
Para que a aplicação funcione corretamente, deve ser criado um schema vazio no MySQL chamado gbiblioteca.

Outra opção é restaurar o backup com o dump do banco de dados do MySQL, já contendo uma massa de dados para testes (livros e usuários cadastrados, alguns empréstimos já efetuados).

 

Interface com o Usuário:
Esta implementação apresenta uma Interface com Usuário em modo console.

O Sistema deve ser iniciado pelo método main() da classe GerenciadorBiblioteca, dentro do pacote br.com.fiap.persistencia.scj16.martins.robson.ui.

 

Modo debug:
A classe GenericDAO (GenericDAO.java) possui um atributo chamado debugInfo, que por padrão está definido como false. Quando colocado em true, informações de debug (nomes das classes especializadas do GenericDAO e StackTraces de Exceptions) são escritos no console (stdout).

 

Fluxo de Operação:
Para operar o Sistema de Gerenciamento de Biblioteca, deve-se seguir o fluxo:

Cadastrar Livros;
Adicionar Exemplares de Livros ao Estoque;
Cadastrar Usuários;
Realizar Empréstimos e Devoluções.
As consultas poderão ser realizadas a qualquer momento.

O backup (dump) do Banco de Dados fornecido contém 321 Usuários, 76 Livros, 274 Exemplares (total) correntemente em Estoque, e 7 Empréstimos já realizados. Ele pode poupar o trabalho de testes do Sistema...


Cadastro de Categorias e Editoras:
Nesta implementação, não existe um Cadastro explícito para Categorias e nem para Editoras. Ao cadastrar um Livro, deve ser informada a Categoria e a Editora.

Se uma Categoria ou Editora já existe, o Sistema não replica esta informação, ele reutiliza a que já está cadastada. Se não existe, ele automaticamente cadastra a Categoria ou Editora como nova.

Quando um Livro é excluido do cadastro, a sua Categoria e a sua Editora não são removidas do cadastro, pois podem ser reutilizadas mais tarde durante o cadastro de outro Livro.


Cadastro de Usuários:
Ao cadastrar um novo Usuário, o Sistema verifica se o nome já existe, neste caso não é criado um novo Usuário com o nome duplicado.


Empréstimo de Livros:
O Empréstimo de Livros foi implementado usando a estrutura original sugerida no arquivo da especificação do exercício, ou seja, EmprestimoID possui somente Livro e Usuario como atributos.

Desta forma, um livro poderá ser emprestado a um usuário somente uma vez, independente das datas de empréstimo e/ou devolução.

Uma possível melhoria para uma futura versão seria a criação de um ID de empréstimo, e a implementação de uma lógica que pudesse habilitar o empréstimo de um segundo livro ao usuário somente se o primeiro já tivesse sido devolvido.
