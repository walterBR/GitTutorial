A árvore git deste tutorial está estrutura da seguinte forma:
<<<<<<< HEAD
atualiza;áo
=======
O Passo a Passo para Criar um Histórico Não Linear
Vamos seguir a sua hierarquia: PMS ?? Sprint ?? TNM.

1. Mesclando sua Tarefa (PMS) na Branch da Sprint (S4025)
Cenário: Você terminou todo o seu trabalho na sua branch PMS-123 e quer integrá-la à branch S4025.

Vá para a branch que vai receber o merge. Neste caso, a branch da Sprint.

Bash

git switch S4025
Sempre atualize a branch receptora. Isso garante que você está juntando seu trabalho com a versão mais recente do código da equipe.

Bash

git pull origin S4025
Execute o MERGE com a flag --no-ff (No Fast-Forward).
Esta flag é a chave para o que você quer. Ela força o Git a criar um merge commit, mesmo que fosse possível simplesmente "avançar" a branch. É isso que cria o "nó" e a linha paralela no gráfico.

Bash

git merge PMS-123 --no-ff
Envie o resultado para o servidor. Agora o histórico não linear estará visível para todos.

Bash

git push origin S4025
O resultado visual será exatamente o que você descreveu:

      o---o---o--\   <-- PMS-123
     /           \
...---o-------------o----o   <-- S4025 (com o novo merge commit)
2. Mesclando a Sprint (S4025) na TNM
Cenário: A sprint de 15 dias acabou. A branch S4025 contém o trabalho de várias tarefas PMS e está estável, pronta para ser integrada à TNM.

O processo é exatamente o mesmo, apenas mudando os nomes das branches:

Vá para a branch TNM:

Bash

git switch TNM
Atualize a TNM:

Bash

git pull origin TNM
Execute o merge forçando a criação do commit:

Bash

git merge S4025 --no-ff
Envie a TNM atualizada:

Bash

git push origin TNM
O resultado visual será um gráfico ainda mais rico:

      o---o---o--\         /
     /           \       /
...---o-------------o----o--------o  <-- TNM (com o merge da Sprint)
                     \          /
                      o---o----o   <-- S4025
>>>>>>> origin/capitulo_3
