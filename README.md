
# Tradução Automática - Seção 9.5 do Dive into Deep Learning

Este repositório contém a implementação do estudo de caso da seção 9.5 do livro *Dive into Deep Learning*, que aborda um sistema de tradução automática entre inglês e francês.

## Respostas da seção 9.5.7

### 1. Como o valor de `num_examples` afeta os tamanhos do vocabulário?

Ao variar o argumento `num_examples` na função `load_data_nmt`, observamos que os tamanhos dos vocabulários tanto do idioma de origem (inglês) quanto do destino (francês) aumentam proporcionalmente com a quantidade de exemplos utilizados.

Isso acontece porque mais exemplos expõem o modelo a um maior número de palavras únicas. Quando usamos, por exemplo, apenas 100 exemplos, muitos termos raros não aparecem e são excluídos pelo `min_freq=2`. Já com 1000 exemplos, o vocabulário abrange muito mais variações lexicais.

Essa relação é importante pois vocabulários maiores aumentam o custo computacional e a complexidade do modelo, além de aumentar a chance de *overfitting* em modelos pequenos. Em contrapartida, vocabulários muito pequenos podem prejudicar a capacidade do modelo de generalizar.

---

### 2. A tokenização em nível de palavra é adequada para idiomas como chinês e japonês?

Não, a tokenização em nível de palavra **não é a melhor abordagem** para idiomas como chinês e japonês. Isso ocorre porque essas línguas não usam espaços para separar palavras, e o conceito de "palavra" pode ser mais fluido do que em línguas como inglês ou português.

Usar tokenização em nível de palavra nesses casos exigiria um sistema complexo de segmentação que pode introduzir erros. Alternativas melhores incluem:

- **Tokenização por caracteres**, que evita ambiguidades na separação.
- **Subword tokenization** (como BPE ou WordPiece), que lida bem com morfologia rica e vocabulário aberto.

**Referência:** Seção 9.5 do *Dive into Deep Learning*, que menciona como a tokenização pode variar entre línguas e contextos.
