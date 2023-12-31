## Workflow com 2 Branches (Master e Homolog)

Este documento descreve o fluxo de trabalho a ser seguido para desenvolvimento, teste e homologação de novas funcionalidades, utilizando as branches "master" e "homolog". Além disso, detalha as nomenclaturas padrão para os tipos de commit e a estrutura de nomenclatura das branches.

**1. Criação das Branches:**

- Verifique se a branch "homolog" já existe:
  ```bash
   git branch --list
   ```
Verifique no retorno se a branch homolog já existe, pule o próximo comando, mas se ela não for listada com o comando acima utilize o comando:
 ```bash
   git checkout -b homolog
   ```
Com isso, sua branch será criada...

- Crie uma nova branch a partir da branch "master":
  ```bash
  git checkout master
  git pull origin master
  git checkout -b idticket_nomeusuario_tipo
  ```
  por exemplo: 6_david_doc.

**2. Preparação para Desenvolvimento:**
- Mantenha a sua branch atualizada com as mudanças da "master" e crie uma relação de acompanhamento (tracking) com ela:
  ```bash
  git checkout idticket_nomeusuario_tipo
  git pull origin master
  git branch --set-upstream-to=origin/master master
  ```
- Resolva quaisquer conflitos que possam ocorrer durante o pull ou durante o merge.

- **3. Desenvolvimento na Nova Branch:**
- Trabalhe na nova branch, implementando as mudanças necessárias.
- Realize commits locais à medida que avança no desenvolvimento:
  ```bash
  git add .
  git commit -m "feat: descrição da alteração"
  ```

**4. Commits e Nomenclaturas Padrão:**
- Utilize as seguintes nomenclaturas de commit:
  - `feat`: Nova feature ou recurso.
  - `fix`: Resolução de um bug.
  - `style`: Atualizações relacionadas à estilização.
  - `refactor`: Refatoração de uma seção específica do código.
  - `test`: Mudanças relacionadas a testes.
  - `docs`: Alterações na documentação.
  - `chore`: Manutenção regular do código.

**5. Merge na Branch de Homologação:**

Certifique-se de estar na sua branch de trabalho:
  
         git checkout idticket_nomeusuario_tipo 
      
Atualize a sua branch de trabalho com as mudanças da "master" (se ainda não o fez):

          git pull origin master
      
Mude para a branch de homologação (substitua `homolog` pelo nome da sua branch de homologação, se for diferente):

         git checkout homolog
      
Faça um merge da sua branch de trabalho na branch de homologação:

         git merge idticket_nomeusuario_tipo
      
Resolva quaisquer conflitos que possam surgir durante o merge.Após resolver os conflitos, faça um push das alterações para a branch de homologação no repositório remoto:
      
         git push origin homolog
   
Após a execução do comando, teremos esse retorno:


  ![image](https://github.com/davidconvergencia/fluxo-git/assets/139790204/b0b10ab3-312c-47c8-80fc-d75873d69970)


         
Clique no link gerado ou copie e cole no navegador e siga os passos indicando o revisor e gere a PullRequest.

**7. Revisão e Aprovação:**
- Um outro menbro da equipe ficará encarregado da revisão do código, este deve analisar o PR e aprovará se as mudanças forem aceitáveis.

**8. Deploy em Ambiente de Homologação:**
- As mudanças aprovadas serão implantadas em um ambiente de homologação, inicialmente de forma manual usando o Filezilla.

**9. Validação e Testes Finais:**
- A equipe de desenvolvimento e qualidade realizará testes abrangentes no ambiente de homologação e após aprovação dos stakeholders as alterações seguirão para esteira de Deploy.

**10. Deploy em Produção (Opcional):**
- Se todos os testes forem bem-sucedidos, as alterações podem ser mescladas da branch de homologação para a branch "master":
  ```bash
  git checkout master
  git merge homolog
  ```


