## BUSCA POR SIMILARIDADE EM ACÓRDÃOS DO CARF

Datasets e notebooks Jupyter criados no Trabalho de Conclusão de Curso (TCC) apresentado ao Curso de Especialização em Ciência de Dados e Big Data da Pontifícia Universidade Católica de Minas Gerais (PUCMinas) como requisito parcial à obtenção do título de especialista.

### Descrição e fonte dos datasets:

a) "Acordaos2020": 35.887 acórdãos publicados pelo CARF em 2020.  
Fonte: NOGALI, Patrick. Arquivos utilizados para o trabalho de conclusão de curso da pós graduação em Ciência de Dados e Big Data da PUC minas. Disponível em: https://github.com/PatrickNogali/TCC-PUC-minas  
Em razão de seu tamanho e do limite imposto pelo GitHub (100 MB), o dataset "Acordaos2020" foi compactado e dividido em dois arquivos, "Acordaos2020.zip.001" e "Acordaos2020.zip.002" por meio do software livre 7-Zip, disponível em https://www.7-zip.org/. O mesmo software deve ser utilizado para a reconstrução do arquivo original, após o download de suas partes.

b) "sumulas": 158 súmulas do CARF vigentes em jul/2021, contendo número da súmula, enunciado e respectivos números de acórdãos precedentes.  
Fonte: web scraping da página "Quadro Geral de Súmulas" do CARF, alcançada a partir de https://carf.economia.gov.br/, menu esquerdo "Jurisprudência", "Súmulas CARF", “Súmulas Consolidadas com os Acórdãos Precedentes”.

c) "precedentes": 405 acórdãos precedentes de súmulas do CARF, contendo os campos número do acórdão, ementa, relatório, voto (relator) e voto vencedor (quando houver).  
Fonte: web scraping da página de pesquisa de acórdãos do CARF, alcançada pelo menu esquerdo "Jurisprudência", "Acórdãos CARF", "Pesquisa de Acórdãos", até o download do arquivo PDF contendo o texto integral do acórdão.

### Descrição dos notebooks (Python 3.8):

#### _1_scraping_sumulas
Obter do sítio do CARF a relação de súmulas aprovadas e vigentes, seu enunciado e respectivos números de acórdãos precedentes.

#### _2_scraping_acordaos
Dado um número de acórdão precedente de súmula, originado do dataset "sumulas" criado pelo notebook _1_scraping_sumulas, baixar o respectivo arquivo PDF do sítio do CARF.

#### _3_xml_precedentes
A partir de arquivos PDF baixados pelo notebook _2_scraping_acordaos, contendo o inteiro teor de acórdãos precedentes de súmulas, obter o documento XML embutido no PDF (quando houver), extrair os dados de interesse do XML e gerar o dataset "precedentes".

#### _4_tratamento
A partir dos datasets "acordaos2020", "sumulas" e "precedentes", realizar as transformações e integrações necessárias para produzir o dataset "corpus", insumo para os modelos de busca por similaridade.

#### _5_exploracao
Analisar o dataset "corpus" criado no notebook _4_tratamento.

#### _6_metrica
Implementar o cálculo de métricas para aferir o quanto as representações vetoriais de documentos, produzidas por um modelo treinado, refletem suas similaridades.

#### _7_treino_teste
Criar os datasets "treino" e "teste" a partir do dataset "corpus" gerado pelo notebook _4_tratamento.

#### _8_tf_idf
Ajustar o modelo BoW TF-IDF e aferir a qualidade de suas representações vetoriais.
(requer o notebook _6_metrica sob a mesma pasta deste)

#### _9_doc2vec
Treinar o modelo Doc2Vec e aferir a qualidade de suas representações vetoriais.
(requer o notebook _6_metrica sob a mesma pasta deste)
