---
title: Abrindo um pull request
content_type: concept
weight: 10
card:
  name: contribuir
  weight: 40
---

<!-- overview -->

{{< note >}}
**Desenvolvedores de código**: Se você estiver documentando uma nova funcionalidade para uma
versão futura do Kubernetes, consulte
[Documente uma nova funcionalidade](/docs/contribute/new-content/new-features/).
{{< /note >}}

Para contribuir com novas páginas de conteúdo ou melhorar as páginas de conteúdo existentes, abra um pull request (PR).
Certifique-se de seguir todos os requisitos na seção
[Antes de começar](/docs/contribute/new-content/) .

Se a alteração for pequena ou você não estiver familiarizado com o git, leia
[Alterações usando o GitHub](#changes-using-github) para saber como editar uma página.

Se suas alterações forem grandes, leia [Trabalhe a partir de um fork local](#fork-the-repo) para saber como fazer
alterações localmente em seu computador.

<!-- body -->

## Mudanças usando o GitHub

Se você tem menos experiência com fluxos de execução do git, este é um método mais fácil para abrir um pull request.
A figura 1 descreve as etapas e os detalhes estão a seguir.

<!-- See https://github.com/kubernetes/website/issues/28808 for live-editor URL to this figure -->
<!-- You can also cut/paste the mermaid code into the live editor at https://mermaid-js.github.io/mermaid-live-editor to play around with it -->

{{< mermaid >}}
flowchart LR
A([fa:fa-user Novo<br>Contribuidor]) --- id1[(K8s/Website<br>GitHub)]
subgraph tasks[Mudanças usando GitHub]
direction TB
    0[ ] -.-
    1[1. Clique em Edit this page] --> 2[2. Use o editor de markdown<br>no GitHub para fazer mudanças]
    2 --> 3[3. preencha o <br> Propose file change]

end
subgraph tasks2[ ]
direction TB
4[4. selecione Propose file change] --> 5[5. selecione Create pull request] --> 6[6. preencha Open a pull request]
6 --> 7[7. selecione Create pull request] 
end

id1 --> tasks --> tasks2

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
classDef k8s fill:#326ce5,stroke:#fff,stroke-width:1px,color:#fff;
classDef spacewhite fill:#ffffff,stroke:#fff,stroke-width:0px,color:#000
class A,1,2,3,4,5,6,7 grey
class 0 spacewhite
class tasks,tasks2 white
class id1 k8s
{{</ mermaid >}}

Figure 1. Etapas para abrir um PR usando o GitHub.

1. Na página onde você vê o issue, selecione o ícone de lápis no canto superior direito.
   Você também pode rolar até a parte inferior da página e selecionar **Edit this page**.

2. Faça suas alterações no editor de markdown do GitHub.

3. Abaixo do editor, preencha o formulário **Propose file change**.
   No primeiro campo, dê um título ao seu commit.
   No segundo campo, forneça uma descrição.
   
   {{< note >}}
   não use nenhuma [palavra-chave do GitHub](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword)
   no seu commit. Você pode adicioná-las à descrição do pull request depois.
   {{< /note >}}

4. Selecione **Propose file change**.

5. Selecione **Create pull request**.

6. A tela **Open a pull request** aparecerá. Preencha o formulário:

   - O campo **Subject** do pull request automaticamente exibe o resumo do commit.
     Você pode alterá-lo, se necessário.
   - O **Corpo** contém a mensagem do seu commit por extenso, caso você tiver uma,
     e um texto padrão. Adicione
     os detalhes necessários e depois remova o texto padrão.
   - Deixe o campo de seleção **Allow edits from maintainers** marcado.

   {{< note >}}
   as descrições do PR são uma ótima maneira de ajudar os revisores a entenderem sua alteração.
   Para mais informações, consulte [Abrindo um PR](#open-a-pr).
   {{</ note >}}

1. Selecione **Create pull request**.

### Recebendo feedback no GitHub

Antes de fazer o merge de um pull request, os membros da comunidade do Kubernetes devem revisá-lo e aprová-lo.
O `k8s-ci-robot` sugere revisores baseado no dono mencionado na página mais próximo.
Se você tem alguém específico em mente, deixe um comentário com o nome de usuário do GitHub da pessoa em mente.

Se um revisor solicitar que você faça alterações:

1. Vá para a aba **Files changed**.
1. Selecione o ícone de lápis (editar) em todos os arquivos alterados pelo pull request.
1. Faça as alterações solicitadas.
1. Confirme as alterações fazendo um commit.

Se você estiver esperando por um revisor, entre em contato uma vez a cada 7 dias. Você também pode postar uma mensagem no
`#sig-docs` canal do Slack.

Quando sua revisão estiver concluída, um revisor fará um merge do seu PR e suas alterações serão publicadas depois de alguns minutos.

## Trabalhe a partir de um fork local {#fork-the-repo}

Se você tiver experiência com o git ou se suas alterações forem maiores do que algumas linhas, trabalhe em um fork local.

Certifique-se de ter o [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) instalado no seu computador.
Você também pode usar uma interface de aplicação do git.

A figura 2 mostra as etapas a serem seguidas quando trabalhando em um fork local. Os detalhes de cada etapa estão a seguir.

<!-- See https://github.com/kubernetes/website/issues/28808 for live-editor URL to this figure -->
<!-- You can also cut/paste the mermaid code into the live editor at https://mermaid-js.github.io/mermaid-live-editor to play around with it -->

{{< mermaid >}}
flowchart LR
1[Faça um fork do repositório<br>do K8s/website] --> 2[Crie um clone local<br>e defina-o upstream]
subgraph changes[Suas alterações]
direction TB
S[ ] -.-
3[Crie uma branch<br>exemplo: minha_nova_branch] --> 3a[Faça alterações usando<br>o editor de texto] --> 4["Veja as alterações<br>localmente usando Hugo<br>(localhost:1313) ou<br>construa uma imagem do contêiner"]
end
subgraph changes2[Commit / Push]
direction TB
T[ ] -.-
5[Faça um commit das alterações] --> 6[Faça um push do commit para<br>origin/minha_nova_branch]
end

2 --> changes --> changes2

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
classDef k8s fill:#326ce5,stroke:#fff,stroke-width:1px,color:#fff;
classDef spacewhite fill:#ffffff,stroke:#fff,stroke-width:0px,color:#000
class 1,2,3,3a,4,5,6 grey
class S,T spacewhite
class changes,changes2 white
{{</ mermaid >}}

Figura 2. Trabalhando a partir de um fork local para fazer suas alterações.

### Faça um fork do repositório kubernetes/website

1. Navegue até o repositório [`kubernetes/website`](https://github.com/kubernetes/website/).
2. Selecione **Fork**.

### Crie um clone local e defina-o upstream

1. Em uma janela de terminal, clone seu fork e atualize o [tema Docsy Hugo](https://github.com/google/docsy#readme):

   ```shell
   git clone git@github.com/<nome_usuário_github>/website
   cd website
   git submodule update --init --recursive --depth 1
   ```

2. Navegue até o novo diretório `website`. Defina o `kubernetes/website` repositório como `upstream` remoto:

   ```shell
   cd website

   git remote add upstream https://github.com/kubernetes/website.git
   ```

3. Confirme seus repositórios `origin` e `upstream`:

   ```shell
   git remote -v
   ```

   O output deve ser semelhante a:

   ```none
   origin	git@github.com:<github_username>/website.git (fetch)
   origin	git@github.com:<github_username>/website.git (push)
   upstream	https://github.com/kubernetes/website.git (fetch)
   upstream	https://github.com/kubernetes/website.git (push)
   ```

4. Faça um fetch dos commits dos forks `origin/main` e `kubernetes/website` via `upstream/main`:

   ```shell
   git fetch origin
   git fetch upstream
   ```

   Isso garante que seu repositório local esteja atualizado antes que você começe a fazer alterações.

   {{< note >}}
   Esse fluxo de execução é diferente do 
   [fluxo de execução GitHub da comunidade do Kubernetes](https://github.com/kubernetes/community/blob/master/contributors/guide/github-workflow.md).
   Você não precisa mesclar sua cópia local `main` com `upstream/main` antes de enviar atualizações para seu fork.
   {{< /note >}}

### Crie uma branch

1. Decida em qual base da branch você trabalhará:

   - Para melhorias no conteúdo existente, use `upstream/main`.
   - Para conteúdo novo sobre recursos existentes, use `upstream/main`.
   - Para traduções, use as convenções de localização. Para mais informações, consulte a 
     [documentação de localização do Kubernetes](/docs/contribute/localization/).
   - Para novas funcionalidades em uma próxima versão do Kubernetes, use a branch de funcionalidades. Para mais informações, consulte [a documentação de uma nova versão](/docs/contribute/new-content/new-features/).
   - Para esforços de longa duração em que vários colaboradores do SIG Docs colaboram, como reorganização de conteúdo, use uma branch de funcionalidades específica criada para esse esforço.

   Se precisar de ajuda para escolher uma branch, pergunte no `#sig-docs` canal do Slack.

2. Crie uma nova branch com base na branch identificada na etapa 1.  Este exemplo assume que a branch base é `upstream/main`:

   ```shell
   git checkout -b <my_new_branch> upstream/main
   ```

3. Faça suas alterações usando um editor de texto.

A qualquer momento, use o commando `git status` para ver quais arquivos você alterou.

### Faça um commit das suas alterações

Quando estiver pronto para abrir um pull request, confirme suas alterações.

1. Em seu repositório local, verifique quais arquivos precisam ser feitos um commit:

   ```shell
   git status
   ```

   O resultado é similar a:

   ```none
   On branch <minha_nova_branch>
   Your branch is up to date with 'origin/<minha_nova_branch>'.

   Changes not staged for commit:
   (use "git add <arquivo>..." to update what will be committed)
   (use "git checkout -- <arquivo>..." to discard changes in working directory)

   modified:   content/en/docs/contribute/new-content/contributing-content.md

   no changes added to commit (use "git add" and/or "git commit -a")
   ```

2. Adicione os arquivos listados em **Changes not staged for commit** ao commit:

   ```shell
   git add <nome_do_seu_arquivo>
   ```

   Repita isso para cada arquivo.

1. Depois de adicionar todos os arquivos, faça um commit:

   ```shell
   git commit -m "Sua mensagem de commit"
   ```

   {{< note >}}
   não use nenhuma [palavra-chave do GitHub](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword)
   em sua mensagem de commit. Você pode adicioná-las à descrição do pull request posteriormente.
   {{< /note >}}

3. Faça um push da sua branch local e seu novo commit para seu fork remoto:

   ```shell
   git push origin <minha_nova_branch>
   ```

### Visualize suas alterações localmente {#preview-locally}

É uma boa ideia visualizar suas alterações localmente antes de fazer um push ou abrir uma pull request.
Uma visualização permite detectar erros de compilação ou problemas de formatação de markdown.

Você pode criar a imagem do contêiner do site ou executar o Hugo localmente. A construção da imagem do contêiner é mais lenta, mas exibe [códigos de acesso Hugo](/docs/contribute/style/hugo-shortcodes/), que podem ser úteis para depuração.

{{< tabs name="tab_with_hugo" >}}
{{% tab name="Hugo em um contêiner" %}}

{{< note >}}
Os comandos abaixo usam o Docker como mecanismo de contêiner padrão. Defina a variável de ambiente `CONTAINER_ENGINE` para substituir esse comportamento.
{{< /note >}}

1. Crie a imagem do contêiner localmente  
   _Você só precisa desta etapa se estiver testando uma alteração na própria ferramenta Hugo_

   ```shell
   # Execute isto em um terminal (se necessário)
   make container-image
   ```

2. Inicie o Hugo em um contêiner:

   ```shell
   # Execute isto em um terminal
   make container-serve
   ```

3. Em um navegador da Web, navegue até `https://localhost:1313`. Hugo observa as mudanças e reconstrói o site conforme necessário.

4. Para interromper a instância local do Hugo, volte ao terminal e digite `Ctrl+C`,
ou feche a janela do terminal.

{{% /tab %}}
{{% tab name="Hugo na linha de comando" %}}

Como alternativa, instale e use o comando `hugo` em seu computador:

1. Instale a versão do [Hugo](https://gohugo.io/getting-started/installing/) especificada em
   [`website/netlify.toml`](https://raw.githubusercontent.com/kubernetes/website/main/netlify.toml).

2. Se você não atualizou o repositório do site, o `website/themes/docsy` diretório deve estar vazio.
   O site não pode ser construído sem uma cópia local do tema. Para atualizar o tema do site, execute:

   ```shell
   git submodule update --init --recursive --depth 1
   ```

3. Em um terminal, acesse o repositório do site do Kubernetes e inicie o servidor Hugo:

   ```shell
   cd <caminho_para_seu_repositório>/website
   hugo server --buildFuture
   ```

4. Em um navegador da Web, navegue até `https://localhost:1313`. Hugo observa as mudanças e reconstrói o site conforme necessário.

5. Para interromper a instância local do Hugo, volte ao terminal e digite `Ctrl+C`,
   ou feche a janela do terminal.

{{% /tab %}}
{{< /tabs >}}

### Abra um pull request do seu fork para o kubernetes/website {#open-a-pr}

A Figura 3 mostra as etapas para abrir um PR do seu fork para o K8s/site. Os detalhes seguem.

<!-- See https://github.com/kubernetes/website/issues/28808 for live-editor URL to this figure -->
<!-- You can also cut/paste the mermaid code into the live editor at https://mermaid-js.github.io/mermaid-live-editor to play around with it -->

{{< mermaid >}}
flowchart LR
subgraph first[ ]
direction TB
1[1. Vá para o repositório do K8s/site] --> 2[2. Selecione 'New Pull Request']
2 --> 3[3. Selecione 'compare across forks']
3 --> 4[4. Selecione seu fork no menu<br>suspenso do seu repositório principal]
end
subgraph second [ ]
direction TB
5[5. Selecione sua branch do<br> menu suspenso 'compare'] --> 6[6. Selecione 'Create Pull Request']
6 --> 7[7. Addicione uma descrição<br>ao seu PR]
7 --> 8[8. Selecione 'Create pull request']
end

first --> second

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
class 1,2,3,4,5,6,7,8 grey
class first,second white
{{</ mermaid >}}

Figure 3. Etapas para abrir um PR do seu fork para o K8s/site.

1. Em um navegador da Web, acesse o repositório [`kubernetes/website`](https://github.com/kubernetes/website/).
1. Selecione **New Pull Request**.
1. Selecione **compare across forks**.
1. No menu suspenso do **repositório principal**, selecione seu fork.
1. No menu suspenso de **comparação** selecione sua branch.
1. Selecione **Create Pull Request**.
1. Adicione uma descrição para seu pull request:

    - **Título** (50 caracteres ou menos): Resuma a intenção por trás da alteração.
    - **Descrição**: Descreva a alteração com mais detalhes.

      - Se houver um problema relacionado ao GitHub, inclua `Fixes #12345` ou `Closes #12345` na descrição. A automação do GitHub fecha o problema mencionado após fazer um merge do PR, se tiver sido usado. Se houver outros PRs relacionados, vincule-os também.
      - Se você quiser conselhos sobre algo específico, inclua as perguntas sobre as quais gostaria que os revisores refletissem na descrição.

1. Selecione o botão **Create pull request**.

Parabéns! Seu pull request está disponível em [Pull requests](https://github.com/kubernetes/website/pulls).

Depois de abrir um PR, o GitHub executa testes automatizados e tenta implantar uma visualização usando o 
[Netlify](https://www.netlify.com/).

- Se a compilação do Netlify falhar, selecione **Details** para obter mais informações.
- Se a compilação do Netlify for bem-sucedida, selecione **Details** para abrir uma versão teste do site do Kubernetes com suas alterações aplicadas. É assim que os revisores verificam suas alterações.

O GitHub também atribui rótulos automaticamente a um PR para ajudar os revisores. Você também pode adicioná-los, se necessário. Para obter mais informações, consulte [Adicionando e removendo rótulos de issues](/docs/contribute/review/for-approvers/#adding-and-removing-issue-labels).

### Abordando feedback localmente

1. Depois de fazer suas alterações, emende seu commit anterior:

   ```shell
   git commit -a --amend
   ```

   - `-a`: inclui todas alterações em um commit 
   - `--amend`: emenda o commit anterior, em vez de criar um novo

2. Atualize sua mensagem de commit, se necessário.

3. Use `git push origin <minha_nova_branch>` para fazer um push de suas alterações e executar novamente os testes do Netlify.

   {{< note >}}
   se você usar `git commit -m` ao invés de emendar, você deverá fazer um [squash dos commits](#squashing-commits) antes de fazer um merge.
   {{< /note >}}

#### Alterações dos revisores

Às vezes, os revisores fazem um commit no seu pull request. Antes de fazer qualquer outra alteração, agregue esses commits.

1. Busque (fetch) os commits do seu fork remoto e faça o rebase da sua branch em uso:

   ```shell
   git fetch origin
   git rebase origin/<nome_da_sua_branch>
   ```

1. Após o rebasing, force um push das novas alterações em seu fork:
   ```shell
   git push --force-with-lease origin <nome_da_sua_branch>
   ```

#### Fazer o merge de conflitos e rebase

{{< note >}}
Para mais informações, consulte [Git Branching - Básico de Branching e Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts),
[Merging Avançado](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging), ou peça ajuda no canal do Slack 
`#sig-docs`.
{{< /note >}}

Se outro colaborador fizer alterações e commits no mesmo arquivo em outro PR, isso poderá criar um conflito de merge. Você deve resolver todos os conflitos de merge em seu PR.

1. Atualize seu fork e rebase sua branch local:

   ```shell
   git fetch origin
   git rebase origin/<nome_da_sua_branch>
   ```

   Em seguida, force as alterações no seu fork:

   ```shell
   git push --force-with-lease origin <nome_da_sua_branch>
   ```

2. Faça um fetch das alterações de `kubernetes/website` `upstream/main` e faça um rebase da sua branch:

   ```shell
   git fetch upstream
   git rebase upstream/main
   ```

3. Inspecione os resultados do rebase:

   ```shell
   git status
   ```

   Isso resulta em vários arquivos marcados como conflitantes.

4. Abra cada arquivo em conflito e procure os marcadores de conflito: `>>>`, `<<<`, e `===`.
   Resolva o conflito e exclua o marcador de conflito.

   {{< note >}}
   Para mais informações, consulte [Como os conflitos são apresentados](https://git-scm.com/docs/git-merge#_how_conflicts_are_presented).
   {{< /note >}}

5. Adicione os arquivos ao changeset:

   ```shell
   git add <nome_do_arquivo>
   ```

6. Continue o rebase:

   ```shell
   git rebase --continue
   ```

7. Repita os passos 2 a 5 conforme necessário.

   Depois de aplicar todos os commits, o comando `git status` mostra que o rebase está completo.

8. Force um push da branch para o seu fork:

   ```shell
   git push --force-with-lease origin <nome_da_sua_branch>
   ```

   O pull request não deve mostrar mais nenhum conflito.

### Squashing commits

{{< note >}}
Para mais informações, consulte [Ferramentas Git - Reescreve o histórico](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History),
ou peça ajuda no canal do Slack `#sig-docs`.
{{< /note >}}

Se seu PR tiver vários commits, você deve fazer um squash em um único commit antes de fazer um merge do seu PR.
Você pode verificar o número de commits na guia de **Commits** do seu PR ou executando localmente o comando `git log`.

{{< note >}}
Este tópico assume `vim` como editor de texto de linha de comando.
{{< /note >}}

1. Inicie um rebase interativo:

   ```shell
   git rebase -i HEAD~<número_de_commits_na_branch>
   ```

   Fazer o squash de commits é uma forma de rebase. O `-i` diz ao git que você deseja fazer o rebase interativamente.
   `HEAD~<número_de_commits_na_branch>` indica quantos commits devem ser observados para o rebase.

   O resultado deve ser semelhante à:

   ```none
   pick d875112ca Original commit
   pick 4fa167b80 Address feedback 1
   pick 7d54e15ee Address feedback 2

   # Rebase 3d18sf680..7d54e15ee onto 3d183f680 (3 commands)

   ...

   # Estas linhas podem ser reorganizadas; elas são executadas de cima para baixo.
   ```

  A primeira seção de resultados lista os commits do rebase. A segunda seção lista as opções para cada commit. 
  Alterar a palavra `pick` altera o status do commit assim que o rebase for concluído.

   Para fins de rebase, concentre-se em `squash` e `pick`.

   {{< note >}}
   Para mais informações, consulte [Modo Interativo](https://git-scm.com/docs/git-rebase#_interactive_mode).
   {{< /note >}}

2. Comece a editar o arquivo.

   Altere o texto original:

   ```none
   pick d875112ca Original commit
   pick 4fa167b80 Address feedback 1
   pick 7d54e15ee Address feedback 2
   ```

   Para:

   ```none
   pick d875112ca Original commit
   squash 4fa167b80 Address feedback 1
   squash 7d54e15ee Address feedback 2
   ```

   Isso faz um squash dos commits `4fa167b80 Address feedback 1` e `7d54e15ee Address feedback 2` em
   `d875112ca Original commit`, deixando apenas `d875112ca Original commit` como parte da linha do tempo(timeline).

3. Salve e feche o arquivo.

4. Faça um push do seu commit squashed:

   ```shell
   git push --force-with-lease origin <nome_da_branch>
   ```

## Contribua para outros repositórios

O [projeto Kubernetes](https://github.com/kubernetes) contém mais de 50 repositórios. Muitos desses repositórios contêm documentação: texto de ajuda voltado para o usuário, mensagens de erro, referências de API ou comentários de código.

Se você vir um texto que gostaria de melhorar, use o GitHub para pesquisar todos os repositórios na organização do Kubernetes. Isso pode ajudá-lo a descobrir onde abrir seu issue ou PR.

Cada repositório tem seus próprios processos e procedimentos. Antes de registrar um issue ou abrir um PR
leia o `README.md`, `CONTRIBUTING.md`, e `code-of-conduct.md`, daquele repositório, caso eles existam.

A maioria dos repositórios usa um modelos para issues e PR. HDê uma olhada em alguns issues em aberto e PRs para ter uma ideia dos processos dessa equipe. Certifique-se de preencher os modelos com o máximo de detalhes possível ao registrar issues ou PRs.

## {{% heading "whatsnext" %}}

- Leia [Revisão](/docs/contribute/review/reviewing-prs) para saber mais sobre o processo de revisão.
