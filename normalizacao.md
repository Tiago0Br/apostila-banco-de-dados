##  Lista de Conteúdos
[SELECT](./README.md)<br />
[NORMALIZAÇÃO](#)

##  Normalização
<details>
<summary>
FORMAS NORMAIS
</summary>

&emsp;&emsp;[1ª FORMA NORMAL](#1ª-forma-normal)</br>
&emsp;&emsp;[2ª FORMA NORMAL](#2ª-forma-normal)</br>
&emsp;&emsp;[3ª FORMA NORMAL](#3ª-forma-normal)</br>

</details>
Normalização é um processo de modelagem do banco de dados projetando a forma como as informações serão armazenadas a fim de eliminar, ou pelo menos minimizar, a redundância e a ambiguidade de informações no banco de dados.

### 1ª Forma normal

Quando todos os atributos contêm apenas um valor correspondente, singular e não existem grupos com mais de um valor ou repetições.<br />
**Exemplo:**

Clientes
|Código|Nome|Endereco|Fone |
|--|--|--|--|
|10 |Diogo |Rua A, 10 |1111-1111 |
|20 |Fábio |Rua B, 25 |2222-2222<br/> 3333-3333 |
|30 |Ana |Rua C, 32 / Atpo 15 |4444-4444 |

Essa tabela apresenta um único registro com dois telefones. Realizando a 1ª normalização, essa tabela será dividida em duas:

Clientes
|Código|Nome|Endereco|
|--|--|--|
|10 |Diogo |Rua A, 10 |
|20 |Fábio |Rua B, 25 |
|30 |Ana |Rua C, 32 / Atpo 15 |

Fone Clientes
|Código|Fone|
|--|--|
|10 |1111-1111|
|20 |2222-2222|
|20 |3333-3333|
|30 |4444-4444|

---

### 2ª Forma normal

Se todos os campos dependem totalmente da chave primária.<br />
**Exemplo:**

OrdemCompra
|codOrdem|dataOrdem|codFornecedor|codProduto|valorUnitario|qtde produto|subTotal|totalGeral|codFornecedor|nomeFornecedor|codProduto|descricaoProduto|
|--|--|--|--|--|--|--|--|--|--|--|--|
|1 |22/09/2022|1 | 1 | 3000 | 1 | 3000 | 25700 |1 |Diogo |1 |Iphone X|
|2 |22/09/2022|2 | 2 | 2800 | 5 | 14000 | 25700 |2 |Fábio |2 |Notebook Asus|
|3 |22/09/2022|2 | 3 | 2900 | 3 | 8700 | 25700 |3 |Ana |3 |Samsung S12|

Essa tabela possui muitos campos e alguns deles não dependem da chave primária "codOrdem", dessa forma, devem ser criadas novas tabelas para esses campos, ficanco dessa forma:

OrdemCompra
|codOrdem|dataOrdem|codFornecedor|codProduto|valorUnitario|qtde produto|subTotal|totalGeral|
|--|--|--|--|--|--|--|--|
|1 |22/09/2022|1 | 1 | 3000 | 1 | 3000 | 25700 |
|2 |22/09/2022|2 | 2 | 2800 | 5 | 14000 | 25700 |
|3 |22/09/2022|2 | 3 | 2900 | 3 | 8700 | 25700 |

Fornecedor
|codFornecedor|nomeFornecedor|
|--|--|
|1 |Diogo |
|2 |Fábio |
|3 |Ana |

Produto
|codProduto|descricaoProduto|
|--|--|
|1 |Iphone X|
|2 |Notebook Asus|
|3 |Samsung S12|

### 3ª Forma normal

Eliminar campos que não dependem da chave primária daquela tabela e também os campos que são resultados de cálculos.<br />
**Exemplo:**

OrdemCompra
|codOrdem|dataOrdem|codFornecedor|codProduto|valorUnitario|qtde produto|subTotal|totalGeral|
|--|--|--|--|--|--|--|--|
|1 |22/09/2022|1 | 1 | 3000 | 1 | 3000 | 25700 |
|2 |22/09/2022|2 | 2 | 2800 | 5 | 14000 | 25700 |
|3 |22/09/2022|2 | 3 | 2900 | 3 | 8700 | 25700 |

Os campos "subTotal" e "totalGeral" são utilizados para armazenar cálculos realizados, portanto para se adequar a 3ª Forma normal devem ser revidos esses campos.

OrdemCompra
|codOrdem|dataOrdem|codFornecedor|codProduto|valorUnitario|qtde produto|
|--|--|--|--|--|--|
|1 |22/09/2022|1 | 1 | 3000 | 1 |
|2 |22/09/2022|2 | 2 | 2800 | 5 |
|3 |22/09/2022|2 | 3 | 2900 | 3 |

Fornecedor
|codFornecedor|nomeFornecedor|
|--|--|
|1 |Diogo |
|2 |Fábio |
|3 |Ana |

Produto
|codProduto|descricaoProduto|
|--|--|
|1 |Iphone X|
|2 |Notebook Asus|
|3 |Samsung S12|

Para obter o subTotal e totalGeral basta usar o SELECT utilizando funções matemáticas como SUM para realizar o cálculo e obter essas informações, sem precisar armazená-las.

#### Vídeo sobre normalização

[![Normalização de Banco de Dados](https://res.cloudinary.com/marcomontalbano/image/upload/v1664757582/video_to_markdown/images/youtube--TOFZQ5wm1UI-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=TOFZQ5wm1UI "Normalização de Banco de Dados")