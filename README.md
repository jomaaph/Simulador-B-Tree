# Simulador de Árvore B+ — documentação

**Criado por José Ferreira**  
Projecto educativo e de código aberto · 2026

## 1. Sobre o projecto

O Simulador de Árvore B+ é uma aplicação didáctica executada no navegador. O objectivo é ajudar estudantes a compreender a organização de uma árvore B+, a distribuição de chaves, os nós internos, as folhas e as operações fundamentais de pesquisa, inserção e remoção.

O projecto não necessita de servidor, base de dados ou instalação de dependências externas: basta abrir o ficheiro `Simulador_BMais.html` num navegador moderno.

## 2. Objectivos pedagógicos

- Visualizar a diferença entre nós internos e folhas.
- Compreender a função das chaves separadoras.
- Observar a divisão de nós (*split*) durante inserções.
- Estudar redistribuição, fusão (*merge*) e redução da raiz durante remoções.
- Acompanhar a ligação sequencial entre folhas.
- Experimentar diferentes ordens e analisar o efeito na altura e na quantidade de nós.
- Recuar e avançar entre estados para comparar resultados sem reiniciar o exercício.

## 3. Tecnologias

| Tecnologia | Utilização |
|---|---|
| HTML5 | Estrutura da interface |
| CSS3 | Apresentação, layout responsivo e efeitos visuais |
| JavaScript | Estrutura de dados, operações e histórico |
| SVG | Desenho dos nós e ligações da árvore |

A aplicação é autónoma e não usa bibliotecas externas.

## 4. Conceitos fundamentais

### 4.1 Ordem da árvore

Neste simulador, a ordem `m` representa o número máximo de filhos de um nó interno.

- Máximo de filhos por nó interno: `m`.
- Máximo de chaves por nó: `m − 1`.
- Mínimo de filhos de um nó interno que não seja raiz: `ceil(m / 2)`.
- Mínimo de chaves numa folha não-raiz: `ceil((m − 1) / 2)`.

A raiz tem regras especiais: pode ter menos filhos do que os nós internos comuns e, quando fica com apenas um filho, esse filho passa a ser a nova raiz.

**Nota:** diferentes livros e implementações podem adoptar convenções distintas para a palavra “ordem”. Neste projecto, deve ser usada a definição apresentada acima.

### 4.2 Nós internos e folhas

- Os nós internos guardam chaves separadoras e referências para os filhos. Não guardam os registos finais.
- As folhas guardam todas as chaves/registos.
- Todas as folhas devem ficar ao mesmo nível.
- As folhas são ligadas sequencialmente, permitindo percorrer os valores ordenados.

As chaves separadoras representam o primeiro valor da subárvore/filho à sua direita, de acordo com a convenção usada no código.

## 5. Tipos de valores e ordenação

O campo de entrada aceita números e palavras. A ordenação aplicada é:

1. Valores numéricos primeiro, em ordem numérica.
2. Valores de texto depois, em ordem alfabética, respeitando as regras de comparação do locale português.
3. Valores repetidos são permitidos.

Exemplo de sequência ordenada: `2, 10, Angola, Brasil, Luanda`.

A comparação numérica é feita quando o conteúdo corresponde a um número válido. Assim, `10` é comparado numericamente com `2`, e não como texto.

## 6. Funcionalidades

### Inserir
1. Introduza uma chave no campo.
2. Seleccione **Inserir** ou pressione Enter.
3. A aplicação localiza a folha apropriada.
4. A chave é inserida na posição ordenada.
5. Se um nó exceder a capacidade, ocorre divisão (*split*), podendo a divisão propagar-se até à raiz.

### Pesquisar
1. Introduza a chave.
2. Seleccione **Pesquisar**.
3. O simulador percorre os separadores desde a raiz até uma folha.
4. A interface destaca o percurso e informa se a chave existe.

### Remover
1. Introduza a chave.
2. Seleccione **Remover uma ocorrência**.
3. Se a chave existir, é removida uma ocorrência.
4. Se um nó ficar abaixo da ocupação mínima, o algoritmo tenta redistribuir com um irmão; caso não seja possível, funde os nós.
5. Se a raiz ficar com um único filho, a altura da árvore é reduzida.

### Recuar e avançar
- **Recuar** restaura o estado anterior da árvore.
- **Avançar** restaura o estado seguinte, caso exista.
- Se for executada uma nova operação depois de recuar, os estados futuros são descartados e começa um novo ramo de histórico.

### Alterar a ordem
A lista de configuração permite escolher as ordens 3, 4, 5 ou 6. Ao alterar a ordem, os valores existentes são reinseridos para construir uma árvore compatível com a nova configuração.

### Exemplos rápidos
- **Carregar 1 a 10** cria uma árvore de demonstração com as chaves de 1 a 10.
- **Limpar árvore** remove todos os nós e inicia um novo exercício.

## 7. Interface e indicadores

| Elemento | Significado |
|---|---|
| Registos nas folhas | Total de chaves armazenadas nas folhas |
| Altura | Número de níveis da árvore |
| Número de folhas | Quantidade de nós folha |
| Máx. chaves / folha | Capacidade máxima de uma folha (`ordem − 1`) |
| Histórico | Estados e operações que podem ser revisitados |
| Cadeia de folhas | Sequência ordenada das folhas ligadas |

## 8. Como executar

1. Descarregue `Simulador_BMais.html`.
2. Guarde o ficheiro numa pasta local.
3. Abra-o com Google Chrome, Firefox, Edge ou outro navegador moderno.
4. Não é necessária ligação à Internet depois de obter o ficheiro.

Para desenvolver, abra o HTML num editor de código. O CSS e o JavaScript estão incorporados no próprio ficheiro.

## 9. Roteiro de exercícios

### Exercício A — Inserção e divisão
Escolha ordem 4 e insira, um de cada vez: `1, 2, 3, 4, 5, 6, 7, 8, 9, 10`.

Observe:
- Em que inserção ocorre a primeira divisão?
- Quando é criada uma nova raiz?
- Como mudam os separadores?
- Quantas folhas existem no final?

### Exercício B — Pesquisa
Pesquise `7` e depois `15`. Compare o percurso e as mensagens.

### Exercício C — Remoção
Remova `9`. Observe a folha afectada e verifique se ocorre redistribuição ou fusão. Experimente também remover valores de folhas diferentes.

### Exercício D — Histórico
Insira `2` e `3`. Use **Recuar** para voltar ao estado com apenas `2`; depois use **Avançar** para recuperar o estado com `2` e `3`.

### Exercício E — Palavras e valores repetidos
Insira `Angola`, `Brasil`, `Canadá`, `Angola` e `10`. Pesquise e remova uma ocorrência de `Angola`. Observe a ordenação e a contagem.

### Exercício F — Comparação de ordens
Repita uma sequência de inserções com ordem 3 e ordem 5. Compare altura, folhas e distribuição.

## 10. Estrutura técnica do código

O ficheiro único contém quatro áreas principais:

- **Modelo de dados:** nós, chaves, filhos e ligação `next` entre folhas.
- **Operações:** comparação, pesquisa de folha, inserção recursiva, divisão, remoção e reequilíbrio.
- **Histórico:** serialização dos estados e restauração por índice.
- **Apresentação:** cálculo de posições, desenho SVG, indicadores e controlos da interface.

## 11. Limitações e âmbito

Este é um mini-projecto educativo, não um motor de armazenamento nem um SGBD. A árvore existe em memória durante a sessão do navegador; fechar ou actualizar a página reinicia o estado.

O simulador serve para estudo visual e experimentação. Para uso académico formal, recomenda-se comparar os resultados com exercícios resolvidos e validar sequências complexas de remoção, especialmente quando existem chaves repetidas ou várias fusões sucessivas.

A aplicação não representa páginas de disco, buffer pool, endereços físicos, persistência, concorrência ou optimizações de um SGBD real.

## 12. Código aberto e licença

Este projecto é disponibilizado com finalidade educativa e intenção de código aberto. A proposta de licença incluída é a **MIT License**, uma licença permissiva que permite usar, copiar, modificar, distribuir e incorporar o código, inclusive em projectos comerciais, desde que o aviso de copyright e a licença sejam mantidos.

A licença MIT é uma escolha proposta para este mini-projecto. Para que a distribuição fique clara, mantenha o ficheiro `LICENSE` junto do código-fonte e inclua os créditos.

## 13. Créditos

**Criado por José Ferreira**  
Simulador de Árvore B+ — mini-projecto educativo e de código aberto.  
© 2026 José Ferreira.

Contribuições, correcções e melhorias são bem-vindas, desde que respeitem a licença distribuída com o projecto.
