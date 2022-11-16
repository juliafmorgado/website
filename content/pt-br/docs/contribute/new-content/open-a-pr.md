---
title: Abrindo um pull request
content_type: concept
weight: 10
card:
  name: contribuir
  weight: 40
---

<!-- overview -->

{{< Observação >}}
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
   
   {{< Observação >}}
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

   {{< Observação >}}
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

   Isso garante que seu repositório local esteja atualizado antes de você começar a fazer alterações.

   {{< Observação >}}
   Esse fluxo de execução é diferente do 
   [fluxo de execução GitHub da comunidade do Kubernetes](https://github.com/kubernetes/community/blob/master/contributors/guide/github-workflow.md).
   You do not need to merge your local copy of `main` with `upstream/main` before pushing updates
   to your fork.
   {{< /note >}}

### Create a branch

1. Decide which branch base to your work on:

   - For improvements to existing content, use `upstream/main`.
   - For new content about existing features, use `upstream/main`.
   - For localized content, use the localization's conventions. For more information, see
     [localizing Kubernetes documentation](/docs/contribute/localization/).
   - For new features in an upcoming Kubernetes release, use the feature branch. For more
     information, see [documenting for a release](/docs/contribute/new-content/new-features/).
   - For long-running efforts that multiple SIG Docs contributors collaborate on,
     like content reorganization, use a specific feature branch created for that effort.

   If you need help choosing a branch, ask in the `#sig-docs` Slack channel.

1. Create a new branch based on the branch identified in step 1. This example assumes the base
   branch is `upstream/main`:

   ```shell
   git checkout -b <my_new_branch> upstream/main
   ```

1. Make your changes using a text editor.

At any time, use the `git status` command to see what files you've changed.

### Commit your changes

When you are ready to submit a pull request, commit your changes.

1. In your local repository, check which files you need to commit:

   ```shell
   git status
   ```

   Output is similar to:

   ```none
   On branch <my_new_branch>
   Your branch is up to date with 'origin/<my_new_branch>'.

   Changes not staged for commit:
   (use "git add <file>..." to update what will be committed)
   (use "git checkout -- <file>..." to discard changes in working directory)

   modified:   content/en/docs/contribute/new-content/contributing-content.md

   no changes added to commit (use "git add" and/or "git commit -a")
   ```

1. Add the files listed under **Changes not staged for commit** to the commit:

   ```shell
   git add <your_file_name>
   ```

   Repeat this for each file.

1. After adding all the files, create a commit:

   ```shell
   git commit -m "Your commit message"
   ```

   {{< note >}}
   Do not use any [GitHub Keywords](https://help.github.com/en/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword)
   in your commit message. You can add those to the pull request
   description later.
   {{< /note >}}

1. Push your local branch and its new commit to your remote fork:

   ```shell
   git push origin <my_new_branch>
   ```

### Preview your changes locally {#preview-locally}

It's a good idea to preview your changes locally before pushing them or opening a pull request.
A preview lets you catch build errors or markdown formatting problems.

You can either build the website's container image or run Hugo locally. Building the container
image is slower but displays [Hugo shortcodes](/docs/contribute/style/hugo-shortcodes/), which can
be useful for debugging.

{{< tabs name="tab_with_hugo" >}}
{{% tab name="Hugo in a container" %}}

{{< note >}}
The commands below use Docker as default container engine. Set the `CONTAINER_ENGINE` environment
variable to override this behaviour.
{{< /note >}}

1. Build the container image locally  
   _You only need this step if you are testing a change to the Hugo tool itself_

   ```shell
   # Run this in a terminal (if required)
   make container-image
   ```

1. Start Hugo in a container:

   ```shell
   # Run this in a terminal
   make container-serve
   ```

1. In a web browser, navigate to `https://localhost:1313`. Hugo watches the
   changes and rebuilds the site as needed.

1. To stop the local Hugo instance, go back to the terminal and type `Ctrl+C`,
   or close the terminal window.

{{% /tab %}}
{{% tab name="Hugo on the command line" %}}

Alternately, install and use the `hugo` command on your computer:

1. Install the [Hugo](https://gohugo.io/getting-started/installing/) version specified in
   [`website/netlify.toml`](https://raw.githubusercontent.com/kubernetes/website/main/netlify.toml).

1. If you have not updated your website repository, the `website/themes/docsy` directory is empty.
   The site cannot build without a local copy of the theme. To update the website theme, run:

   ```shell
   git submodule update --init --recursive --depth 1
   ```

1. In a terminal, go to your Kubernetes website repository and start the Hugo server:

   ```shell
   cd <path_to_your_repo>/website
   hugo server --buildFuture
   ```

1. In a web browser, navigate to `https://localhost:1313`. Hugo watches the
   changes and rebuilds the site as needed.

1. To stop the local Hugo instance, go back to the terminal and type `Ctrl+C`,
   or close the terminal window.

{{% /tab %}}
{{< /tabs >}}

### Open a pull request from your fork to kubernetes/website {#open-a-pr}

Figure 3 shows the steps to open a PR from your fork to the K8s/website. The details follow.

<!-- See https://github.com/kubernetes/website/issues/28808 for live-editor URL to this figure -->
<!-- You can also cut/paste the mermaid code into the live editor at https://mermaid-js.github.io/mermaid-live-editor to play around with it -->

{{< mermaid >}}
flowchart LR
subgraph first[ ]
direction TB
1[1. Go to K8s/website repository] --> 2[2. Select New Pull Request]
2 --> 3[3. Select compare across forks]
3 --> 4[4. Select your fork from<br>head repository drop-down menu]
end
subgraph second [ ]
direction TB
5[5. Select your branch from<br>the compare drop-down menu] --> 6[6. Select Create Pull Request]
6 --> 7[7. Add a description<br>to your PR]
7 --> 8[8. Select Create pull request]
end

first --> second

classDef grey fill:#dddddd,stroke:#ffffff,stroke-width:px,color:#000000, font-size:15px;
classDef white fill:#ffffff,stroke:#000,stroke-width:px,color:#000,font-weight:bold
class 1,2,3,4,5,6,7,8 grey
class first,second white
{{</ mermaid >}}

Figure 3. Steps to open a PR from your fork to the K8s/website.

1. In a web browser, go to the [`kubernetes/website`](https://github.com/kubernetes/website/) repository.
1. Select **New Pull Request**.
1. Select **compare across forks**.
1. From the **head repository** drop-down menu, select your fork.
1. From the **compare** drop-down menu, select your branch.
1. Select **Create Pull Request**.
1. Add a description for your pull request:

    - **Title** (50 characters or less): Summarize the intent of the change.
    - **Description**: Describe the change in more detail.

      - If there is a related GitHub issue, include `Fixes #12345` or `Closes #12345` in the
        description. GitHub's automation closes the mentioned issue after merging the PR if used.
        If there are other related PRs, link those as well.
      - If you want advice on something specific, include any questions you'd like reviewers to
        think about in your description.

1. Select the **Create pull request** button.

Congratulations! Your pull request is available in [Pull requests](https://github.com/kubernetes/website/pulls).

After opening a PR, GitHub runs automated tests and tries to deploy a preview using
[Netlify](https://www.netlify.com/).

- If the Netlify build fails, select **Details** for more information.
- If the Netlify build succeeds, select **Details** opens a staged version of the Kubernetes
  website with your changes applied. This is how reviewers check your changes.

GitHub also automatically assigns labels to a PR, to help reviewers. You can add them too, if
needed. For more information, see [Adding and removing issue labels](/docs/contribute/review/for-approvers/#adding-and-removing-issue-labels).

### Addressing feedback locally

1. After making your changes, amend your previous commit:

   ```shell
   git commit -a --amend
   ```

   - `-a`: commits all changes
   - `--amend`: amends the previous commit, rather than creating a new one

1. Update your commit message if needed.

1. Use `git push origin <my_new_branch>` to push your changes and re-run the Netlify tests.

   {{< note >}}
   If you use `git commit -m` instead of amending, you must [squash your commits](#squashing-commits)
   before merging.
   {{< /note >}}

#### Changes from reviewers

Sometimes reviewers commit to your pull request. Before making any other changes, fetch those commits.

1. Fetch commits from your remote fork and rebase your working branch:

   ```shell
   git fetch origin
   git rebase origin/<your-branch-name>
   ```

1. After rebasing, force-push new changes to your fork:

   ```shell
   git push --force-with-lease origin <your-branch-name>
   ```

#### Merge conflicts and rebasing

{{< note >}}
For more information, see [Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts),
[Advanced Merging](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging), or ask in the
`#sig-docs` Slack channel for help.
{{< /note >}}

If another contributor commits changes to the same file in another PR, it can create a merge
conflict. You must resolve all merge conflicts in your PR.

1. Update your fork and rebase your local branch:

   ```shell
   git fetch origin
   git rebase origin/<your-branch-name>
   ```

   Then force-push the changes to your fork:

   ```shell
   git push --force-with-lease origin <your-branch-name>
   ```

1. Fetch changes from `kubernetes/website`'s `upstream/main` and rebase your branch:

   ```shell
   git fetch upstream
   git rebase upstream/main
   ```

1. Inspect the results of the rebase:

   ```shell
   git status
   ```

   This results in a number of files marked as conflicted.

1. Open each conflicted file and look for the conflict markers: `>>>`, `<<<`, and `===`.
   Resolve the conflict and delete the conflict marker.

   {{< note >}}
   For more information, see [How conflicts are presented](https://git-scm.com/docs/git-merge#_how_conflicts_are_presented).
   {{< /note >}}

1. Add the files to the changeset:

   ```shell
   git add <filename>
   ```

1. Continue the rebase:

   ```shell
   git rebase --continue
   ```

1. Repeat steps 2 to 5 as needed.

   After applying all commits, the `git status` command shows that the rebase is complete.

1. Force-push the branch to your fork:

   ```shell
   git push --force-with-lease origin <your-branch-name>
   ```

   The pull request no longer shows any conflicts.

### Squashing commits

{{< note >}}
For more information, see [Git Tools - Rewriting History](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History),
or ask in the `#sig-docs` Slack channel for help.
{{< /note >}}

If your PR has multiple commits, you must squash them into a single commit before merging your PR.
You can check the number of commits on your PR's **Commits** tab or by running the `git log`
command locally.

{{< note >}}
This topic assumes `vim` as the command line text editor.
{{< /note >}}

1. Start an interactive rebase:

   ```shell
   git rebase -i HEAD~<number_of_commits_in_branch>
   ```

   Squashing commits is a form of rebasing. The `-i` switch tells git you want to rebase interactively.
   `HEAD~<number_of_commits_in_branch` indicates how many commits to look at for the rebase.

   Output is similar to:

   ```none
   pick d875112ca Original commit
   pick 4fa167b80 Address feedback 1
   pick 7d54e15ee Address feedback 2

   # Rebase 3d18sf680..7d54e15ee onto 3d183f680 (3 commands)

   ...

   # These lines can be re-ordered; they are executed from top to bottom.
   ```

   The first section of the output lists the commits in the rebase. The second section lists the
   options for each commit. Changing the word `pick` changes the status of the commit once the rebase
   is complete.

   For the purposes of rebasing, focus on `squash` and `pick`.

   {{< note >}}
   For more information, see [Interactive Mode](https://git-scm.com/docs/git-rebase#_interactive_mode).
   {{< /note >}}

1. Start editing the file.

   Change the original text:

   ```none
   pick d875112ca Original commit
   pick 4fa167b80 Address feedback 1
   pick 7d54e15ee Address feedback 2
   ```

   To:

   ```none
   pick d875112ca Original commit
   squash 4fa167b80 Address feedback 1
   squash 7d54e15ee Address feedback 2
   ```

   This squashes commits `4fa167b80 Address feedback 1` and `7d54e15ee Address feedback 2` into
   `d875112ca Original commit`, leaving only `d875112ca Original commit` as a part of the timeline.

1. Save and exit your file.

1. Push your squashed commit:

   ```shell
   git push --force-with-lease origin <branch_name>
   ```

## Contribute to other repos

The [Kubernetes project](https://github.com/kubernetes) contains 50+ repositories. Many of these
repositories contain documentation: user-facing help text, error messages, API references or code
comments.

If you see text you'd like to improve, use GitHub to search all repositories in the Kubernetes
organization. This can help you figure out where to submit your issue or PR.

Each repository has its own processes and procedures. Before you file an issue or submit a PR,
read that repository's `README.md`, `CONTRIBUTING.md`, and `code-of-conduct.md`, if they exist.

Most repositories use issue and PR templates. Have a look through some open issues and PRs to get
a feel for that team's processes. Make sure to fill out the templates with as much detail as
possible when you file issues or PRs.

## {{% heading "whatsnext" %}}

- Read [Reviewing](/docs/contribute/review/reviewing-prs) to learn more about the review process.
