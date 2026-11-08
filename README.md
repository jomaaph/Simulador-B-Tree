# Simulador de Árvore B+

Projecto educativo e de código aberto desenvolvido para o estudo interactivo de estruturas de dados avançadas.

---

## 1. Sobre o Projecto

O **Simulador de Árvore B+** é uma aplicação didáctica executada inteiramente no navegador, concebida para ajudar estudantes e entusiastas de ciência de computadores a compreender de forma visual a organização de uma árvore B+. A ferramenta demonstra de maneira clara a distribuição de chaves, o comportamento dos nós internos e folhas, bem como as operações fundamentais de pesquisa, inserção e remoção.

**Vantagens principais:** Totalmente autónomo, sem necessidade de servidores, bases de dados ou instalação de dependências externas — basta abrir o ficheiro HTML num navegador moderno.

---

## 2. Objectivos Pedagógicos

* **Visualização Estrutural:** Distinguir visualmente nós internos (separadores) e nós folha (dados).
* **Operações Dinâmicas:** Acompanhar a divisão de nós (*split*) durante inserções e as fases de redistribuição ou fusão (*merge*) durante remoções.
* **Navegação Sequencial:** Observar a ligação directa entre folhas ordenadas.
* **Flexibilidade de Parâmetros:** Experimentar diferentes ordens de árvore e analisar o impacto directo na altura e quantidade de nós.
* **Controlo de Histórico:** Recuar e avançar entre estados para comparar resultados passo a passo sem perder o fio ao exercício.

---

## 3. Tecnologias Utilizadas

| Tecnologia | Propósito |
| :--- | :--- |
| **HTML5** | Estruturação da interface de utilizador |
| **CSS3** | Estilização, layout responsivo e efeitos visuais limpos |
| **JavaScript** | Lógica da estrutura de dados, gestão de operações e histórico de estados |
| **SVG** | Renderização dinâmica e vectorizada dos nós e ligações da árvore |

---

## 4. Conceitos Fundamentais

### 4.1. Ordem da Árvore ($m$)
A ordem $m$ define os limites estruturais da árvore:
* **Máximo de filhos por nó interno:** $m$.
* **Máximo de chaves por nó:** $m - 1$.
* **Mínimo de filhos de um nó interno** (excepto raiz): $\lceil m / 2 \rceil$.
* **Mínimo de chaves numa folha não-raiz:** $\lceil (m - 1) / 2 \rceil$.

*Nota sobre a Raiz:* Possui regras especiais, podendo ter menos filhos do que os nós comuns. Caso fique com apenas um filho, esse filho é promovido a nova raiz.

### 4.2. Nós Internos vs. Folhas
* **Nós Internos:** Armazenam chaves separadoras e referências para os nós filhos, servindo unicamente de guia para o encaminhamento das pesquisas.
* **Folhas:** Contêm todas as chaves e registos finais, encontrando-se rigorosamente ao mesmo nível e interligadas sequencialmente para percurso eficiente.

---

## 5. Tipos de Valores e Ordenação

O simulador aceita tanto números como palavras, aplicando a seguinte política de ordenação:
1. **Valores numéricos** prioritários, dispostos em ordem numérica estrita.
2. **Valores de texto** subsequentes, ordenados alfabeticamente segundo as regras de comparação do *locale* português.
3. **Valores repetidos** são permitidos sem restrições.

---

## 6. Guia de Funcionalidades

* **Inserir:** Adiciona uma chave respeitando a ordenação. Se a capacidade do nó for excedida, ocorre o *split* propagável até à raiz.
* **Pesquisar:** Percorre os separadores desde a raiz até à folha correspondente, destacando visualmente o caminho percorrido.
* **Remover:** Elimina uma ocorrência da chave, desencadeando redistribuição com irmãos ou fusão de nós caso a ocupação mínima seja quebrada.
* **Histórico (Recuar / Avançar):** Permite navegar iterativamente pelos estados anteriores e posteriores da árvore.
* **Alteração de Ordem:** Disponibiliza selecção dinâmica entre as ordens 3, 4, 5 e 6, reconstruindo automaticamente a árvore com base nos dados existentes.

---

## 7. Roteiro de Exercícios Práticos

* **Exercício A (Inserção e Divisão):** Configure a ordem para 4 e insira sequencialmente os valores de 1 a 10. Observe a formação de divisões e a criação de novas raízes.
* **Exercício B (Pesquisa):** Teste a busca por uma chave existente (ex: `7`) e uma inexistente (ex: `15`) para comparar os percursos visuais.
* **Exercício C (Remoção):** Remova o valor `9` e analise o comportamento de redistribuição ou fusão de nós folhas.
* **Exercício D (Multilinguagem/Tipos):** Insira palavras como `Angola`, `Brasil`, `Canadá` juntamente com números e verifique a ordenação híbrida.

---

## 8. Como Executar

1. Descarregue o ficheiro principal do repositório.
2. Guarde-o numa pasta local no seu computador.
3. Abra-o directamente em qualquer navegador moderno (Google Chrome, Firefox, Microsoft Edge) — não requer servidores nem ligações à Internet.

---

## 9. Licença

Este projecto é disponibilizado sob a licença **MIT**, permitindo o uso, modificação e distribuição livre para fins educativos e comerciais.

---

*Criado por José Ferreira · 2026*
