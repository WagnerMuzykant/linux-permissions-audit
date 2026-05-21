# Auditoria e Gestão de Permissões de Arquivos no Linux 🐧🔐

## 📝 Descrição do Projeto
A equipe de pesquisa da minha organização precisa atualizar as permissões de determinados arquivos e diretórios dentro do diretório `projects`. As permissões atuais não refletem o nível de autorização que deveria ser concedido. Verificar e atualizar essas permissões ajudará a manter o sistema deles seguro.

Neste projeto, realizei uma auditoria de segurança no sistema de arquivos corporativo utilizando o terminal Bash do Linux para garantir o alinhamento com o **Princípio do Privilégio Mínimo**. Identifiquei desvios de conformidade e corrigi as permissões utilizando comandos de controle de acesso (`chmod`).

---

## 🧭 Verificação de Detalhes de Arquivos e Diretórios

O código a seguir demonstra como usei comandos do Linux para determinar as permissões existentes definidas para um diretório específico no sistema de arquivos.

<img width="620" height="203" alt="image" src="https://github.com/user-attachments/assets/8da83e99-5304-408c-b415-ae4e3963be64" />


**Explicação do Comando:**
O código lista todo o conteúdo do diretório `projects`. Utilizei o comando `ls` com a opção `-la` para exibir uma listagem detalhada do conteúdo do arquivo que também retornou arquivos ocultos. A string de 10 caracteres na primeira coluna representa as permissões definidas em cada arquivo ou diretório.

---

## 🔏 Descrição da Cadeia de Permissões
A string de 10 caracteres pode ser desconstruída para determinar quem está autorizado a acessar o arquivo e suas permissões específicas. Tomando como exemplo as permissões do arquivo `project_t.txt`, que são `-rw-rw-r--`:

* **1º caractere (`-`):** Como o primeiro caractere é um hífen (`-`), isso indica que o `project_t.txt` é um arquivo, não um diretório.
* **2º ao 4º caractere (`rw-`):** Estes caracteres indicam as permissões de leitura (`r`), gravação (`w`) e execução (`x`) para o usuário.
* **5º ao 7º caractere (`rw-`):** Estes caracteres indicam as permissões de leitura, gravação e execução para o grupo. O terceiro e o sexto caracteres são `w`, o que indica que apenas o usuário e o grupo têm permissões de gravação.
* **8º ao 10º caractere (`r--`):** Estes caracteres indicam as permissões de leitura, gravação e execução para outros. Ninguém tem permissões de execução para o `project_t.txt`.

---

## 🛠️ Alteração de Permissões de Arquivos e Diretórios

A organização determinou que "outros" não deveriam ter acesso de gravação a nenhum de seus arquivos. Determinei que o `project_k.txt` deve ter o acesso de gravação removido para "outros". O código a seguir demonstra como usei os comandos do Linux para fazer isso:

<img width="622" height="201" alt="image" src="https://github.com/user-attachments/assets/303b4021-25d3-48db-a8de-19458fe564ea" />


**Explicação do Comando:**
O comando `chmod` altera as permissões em arquivos e diretórios. Neste exemplo, removi as permissões de gravação de "outros" para o arquivo `project_k.txt` usando o argumento `o-w`.

### Protegendo um Arquivo Oculto
A equipe de pesquisa da minha organização arquivou recentemente o `.project_x.txt`. Eles não querem que ninguém tenha acesso de gravação a este projeto, mas o usuário e o grupo devem ter acesso de leitura. O código a seguir demonstra como mudei as permissões:

<img width="621" height="215" alt="image" src="https://github.com/user-attachments/assets/e25a588d-22f8-447c-ba34-c8bfc0a8e42b" />


**Explicação do Comando:**
Eu sei que o `.project_x.txt` é um arquivo oculto porque começa com um ponto (`.`). Removi as permissões de gravação do usuário com `u-w`. Em seguida, removi as permissões de gravação do grupo com `g-w` e adicionei permissões de leitura ao grupo com `g+r`.

### Isolando um Diretório Restrito
Minha organização quer que apenas o usuário `researcher2` tenha acesso ao diretório `drafts` e ao seu conteúdo. Isso significa que ninguém além do `researcher2` deve ter permissões de execução. O código a seguir demonstra como usei os comandos do Linux para alterar as permissões:

<img width="623" height="186" alt="image" src="https://github.com/user-attachments/assets/a67833e8-b823-4579-9196-eae647b14d0a" />


**Explicação do Comando:**
Determinei anteriormente que o grupo tinha permissões de execução, então usei o comando `chmod g-x drafts` para removê-las. O usuário `researcher2` já tinha permissões de execução, então elas não precisaram ser adicionadas.

---

## 📊 Resumo Executivo
Alterei múltiplas permissões para corresponder ao nível de autorização que minha organização desejava para arquivos e diretórios no diretório `projects`. 

O primeiro passo nisso foi usar `ls -la` para verificar as permissões para o diretório. Isso informou minhas decisões nas etapas seguintes. Em seguida, usei o comando `chmod` várias vezes para alterar as permissões em arquivos e diretórios, garantindo a segurança do sistema e a aplicação rigorosa do Princípio do Privilégio Mínimo.
