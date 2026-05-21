# Auditoria e Gestão de Permissões de Arquivos no Linux 🐧🔐

## 📝 Descrição do Projeto
[cite_start]A equipe de pesquisa da minha organização precisa atualizar as permissões de determinados arquivos e diretórios dentro do diretório `projects`[cite: 3]. [cite_start]As permissões atuais não refletem o nível de autorização que deveria ser concedido[cite: 4]. [cite_start]Verificar e atualizar essas permissões ajudará a manter o sistema deles seguro[cite: 5].

Neste projeto, realizei uma auditoria de segurança no sistema de arquivos corporativo utilizando o terminal Bash do Linux para garantir o alinhamento com o **Princípio do Privilégio Mínimo**. Identifiquei desvios de conformidade e corrigi as permissões utilizando comandos de controle de acesso (`chmod`).

---

## 🧭 Verificação de Detalhes de Arquivos e Diretórios

[cite_start]O código a seguir demonstra como usei comandos do Linux para determinar as permissões existentes definidas para um diretório específico no sistema de arquivos[cite: 7].

<img width="617" height="200" alt="image" src="https://github.com/user-attachments/assets/db4ba3e2-4567-481d-a687-2a1ef07cebe4" />


**Explicação do Comando:**
[cite_start]O código lista todo o conteúdo do diretório `projects`[cite: 9]. [cite_start]Utilizei o comando `ls` com a opção `-la` para exibir uma listagem detalhada do conteúdo do arquivo que também retornou arquivos ocultos[cite: 10]. [cite_start]A string de 10 caracteres na primeira coluna representa as permissões definidas em cada arquivo ou diretório[cite: 12].

---

## 🔏 Descrição da Cadeia de Permissões
[cite_start]A string de 10 caracteres pode ser desconstruída para determinar quem está autorizado a acessar o arquivo e suas permissões específicas[cite: 14]. [cite_start]Tomando como exemplo as permissões do arquivo `project_t.txt`, que são `-rw-rw-r--`[cite: 25]:

* [cite_start]**1º caractere (`-`):** Como o primeiro caractere é um hífen (`-`), isso indica que o `project_t.txt` é um arquivo, não um diretório[cite: 26].
* [cite_start]**2º ao 4º caractere (`rw-`):** Estes caracteres indicam as permissões de leitura (`r`), gravação (`w`) e execução (`x`) para o usuário[cite: 18].
* [cite_start]**5º ao 7º caractere (`rw-`):** Estes caracteres indicam as permissões de leitura, gravação e execução para o grupo[cite: 20]. [cite_start]O terceiro e o sexto caracteres são `w`, o que indica que apenas o usuário e o grupo têm permissões de gravação[cite: 28].
* [cite_start]**8º ao 10º caractere (`r--`):** Estes caracteres indicam as permissões de leitura, gravação e execução para outros[cite: 22]. [cite_start]Ninguém tem permissões de execução para o `project_t.txt`[cite: 29].

---

## 🛠️ Alteração de Permissões de Arquivos e Diretórios

[cite_start]A organização determinou que "outros" não deveriam ter acesso de gravação a nenhum de seus arquivos[cite: 31]. [cite_start]Determinei que o `project_k.txt` deve ter o acesso de gravação removido para "outros"[cite: 33]. [cite_start]O código a seguir demonstra como usei os comandos do Linux para fazer isso[cite: 34]:

[COLE SEU PRINT DA ALTERAÇÃO DO PROJECT_K AQUI]

**Explicação do Comando:**
[cite_start]O comando `chmod` altera as permissões em arquivos e diretórios[cite: 36]. [cite_start]Neste exemplo, removi as permissões de gravação de "outros" para o arquivo `project_k.txt` usando o argumento `o-w`[cite: 38].

### Protegendo um Arquivo Oculto
[cite_start]A equipe de pesquisa da minha organização arquivou recentemente o `.project_x.txt`[cite: 41]. [cite_start]Eles não querem que ninguém tenha acesso de gravação a este projeto, mas o usuário e o grupo devem ter acesso de leitura[cite: 42]. [cite_start]O código a seguir demonstra como mudei as permissões[cite: 43]:

[COLE SEU PRINT DA ALTERAÇÃO DO PROJECT_X AQUI]

**Explicação do Comando:**
[cite_start]Eu sei que o `.project_x.txt` é um arquivo oculto porque começa com um ponto (`.`)[cite: 45]. [cite_start]Removi as permissões de gravação do usuário com `u-w`[cite: 47]. [cite_start]Em seguida, removi as permissões de gravação do grupo com `g-w` e adicionei permissões de leitura ao grupo com `g+r`[cite: 48].

### Isolando um Diretório Restrito
[cite_start]Minha organização quer que apenas o usuário `researcher2` tenha acesso ao diretório `drafts` e ao seu conteúdo[cite: 50]. [cite_start]Isso significa que ninguém além do `researcher2` deve ter permissões de execução[cite: 51]. [cite_start]O código a seguir demonstra como usei os comandos do Linux para alterar as permissões[cite: 52]:

[COLE SEU PRINT DA ALTERAÇÃO DO DIRETÓRIO DRAFTS AQUI]

**Explicação do Comando:**
[cite_start]Determinei anteriormente que o grupo tinha permissões de execução, então usei o comando `chmod g-x drafts` para removê-las[cite: 54]. [cite_start]O usuário `researcher2` já tinha permissões de execução, então elas não precisaram ser adicionadas[cite: 55].

---

## 📊 Resumo Executivo
[cite_start]Alterei múltiplas permissões para corresponder ao nível de autorização que minha organização desejava para arquivos e diretórios no diretório `projects`[cite: 57]. 

[cite_start]O primeiro passo nisso foi usar `ls -la` para verificar as permissões para o diretório[cite: 58]. Isso informou minhas decisões nas etapas seguintes. [cite_start]Em seguida, usei o comando `chmod` várias vezes para alterar as permissões em arquivos e diretórios[cite: 59], garantindo a segurança do sistema e a aplicação rigorosa do Princípio do Privilégio Mínimo.
