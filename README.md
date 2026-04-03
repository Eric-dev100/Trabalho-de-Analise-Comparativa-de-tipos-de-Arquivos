# Trabalho-de-Analise-Comparativa-de-tipos-de-Arquivos
Benchmark de arquiteturas de Big Data. Análise de desempenho, CPU e RAM em formatos de Texto, Linha, Coluna e Memória (CSV, Parquet, Avro, Arrow e etc) utilizando PySpark e Pandas com +4 milhões de registros reais

#  Pesquisa e Implementação de Dados em Python

**Autores:** Eric Gabriel e Chrysthyan Matheus

Este repositório contém uma pesquisa aplicada e testes de *benchmarking* sobre as principais arquiteturas e categorias de dados utilizadas na Engenharia e Análise de Dados moderna. O objetivo é demonstrar, na prática, como a escolha do formato de armazenamento impacta diretamente o uso de CPU, o consumo de RAM e o tempo de execução (I/O) em pipelines de processamento de alto desempenho.

##  Escopo do Projeto

A pesquisa avalia a eficiência de leitura, escrita e compressão dividindo os formatos em quatro paradigmas principais:

1. **Baseados em Texto:** CSV, XML, JSON.
2. **Baseados em Linha:** Hadoop SequenceFile, Avro.
3. **Baseados em Coluna:** RCFile (Record Columnar File), ORC, Parquet, Carbon Data.
4. **Baseados em Memória:** Apache Arrow (Feather / IPC).

##  Especificações do Dataset

Para garantir a precisão dos testes de *stress*, utilizamos um grande volume de dados governamentais abertos do mundo real:
* **Origem:** Base de Dados Abertos da Polícia Rodoviária Federal (PRF) - Acidentes de Trânsito (2017 a 2025).
* **Volume:** 4.069.582 de linhas processadas e 11 colunas.
* **Tipos de Dados:** Strings, inteiros, floats e datetimes.

##  Metodologia e Tecnologias

* **Stack Principal:** Python 3, Apache Spark (PySpark com suporte nativo ao Hive), PyArrow, Pandas.
* **Monitoramento de Hardware:** Uso da biblioteca `psutil` e `resource` para captura de pico de memória RAM e processamento de CPU durante a conversão e o mapeamento de arquivos.
* **AI-Driven Engineering:** Utilização de Inteligência Artificial para atuar como Assistente de Pesquisa e Analista de Sistemas na interpretação de *IllegalStateExceptions*, na unificação de esquemas fortemente tipados (ex: *casting* rigoroso no Arrow) e na validação conceitual sobre o gerenciamento da JVM e cache L1/L2.

##  Principais Conclusões

*  Formatos em texto plano (como CSV) sofrem severamente com o custo de *parsing* sequencial, impedindo a vetorização e destruindo a eficiência da CPU.
*  Foi possível documentar a transição de formatos primitivos e engessados (SequenceFile, que aceita apenas Chave-Valor) para arquiteturas mais elegantes como o Avro, ideal para integrações de *streaming* fluidas.
*  Formatos legados como o RCFile dependem inteiramente de força bruta para compressão (Zlib/Gzip). Durante o estudo do Parquet/ORC, documentamos como o Acoplamento Forte (*Tight Coupling*) ao ecossistema Hadoop/JVM pode quebrar pipelines em motores modernos.
*  O formato Apache Arrow demonstrou resultados quase instantâneos na leitura graças ao Mapeamento de Memória e ao conceito *Zero-Copy*, aliado a compressões de baixíssima latência como LZ4 e Zstd.
