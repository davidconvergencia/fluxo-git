## Workflow com 2 Branches (Master e Homolog)

Este documento descreve o fluxo de trabalho a ser seguido para desenvolvimento, teste e homologação de novas funcionalidades, utilizando as branches "master" e "homolog". Além disso, detalha as nomenclaturas padrão para os tipos de commit e a estrutura de nomenclatura das branches.

**1. Criação das Branches:**
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

    - Certifique-se de estar na sua branch de trabalho:
         ```bash
         git checkout idticket_nomeusuario_tipo
         ```
      
    - Atualize a sua branch de trabalho com as mudanças da "master" (se ainda não o fez):
         ```bash
         git pull origin master
         ```
      
      3. Mude para a branch de homologação (substitua `homolog` pelo nome da sua branch de homologação, se for diferente):
         ```bash
         git checkout homolog
         ```
      
      4. Faça um merge da sua branch de trabalho na branch de homologação:
         ```bash
         git merge idticket_nomeusuario_tipo
         ```
      
      5. Resolva quaisquer conflitos que possam surgir durante o merge.
      
      6. Após resolver os conflitos, faça um push das alterações para a branch de homologação no repositório remoto:
         ```bash
         git push origin homolog
         ```
      7. Após a execução do comando, teremos esse retorno:
         ![image](https://github.com/davidconvergencia/fluxo-git/assets/139790204/b0b10ab3-312c-47c8-80fc-d75873d69970)
      8. Clique no link gerado ou copie e cole no navegador



**7. Revisão e Aprovação:**
- A equipe de revisão analisará o PR e aprovará se as mudanças forem aceitáveis.

**8. Deploy em Ambiente de Homologação:**
- As mudanças aprovadas serão implantadas em um ambiente de homologação.

**9. Validação e Testes Finais:**
- A equipe de desenvolvimento e qualidade realizará testes abrangentes no ambiente de homologação.

**10. Deploy em Produção (Opcional):**
- Se todos os testes forem bem-sucedidos, as alterações podem ser mescladas da branch de homologação para a branch "master":
  ```bash
  git checkout master
  git merge homolog
  ```
