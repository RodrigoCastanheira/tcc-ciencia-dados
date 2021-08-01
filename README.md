## BUSCA POR SIMILARIDADE EM AC�RD�OS DO CARF

Datasets e notebooks Jupyter criados no Trabalho de Conclus�o de Curso (TCC) apresentado ao Curso de Especializa��o em Ci�ncia de Dados e Big Data da Pontif�cia Universidade Cat�lica de Minas Gerais (PUCMinas) como requisito parcial � obten��o do t�tulo de especialista.

### Descri��o e fonte dos datasets:

a) "Acordaos2020": 35.887 ac�rd�os publicados pelo CARF em 2020.  
Fonte: NOGALI, Patrick. Arquivos utilizados para o trabalho de conclus�o de curso da p�s gradua��o em Ci�ncia de Dados e Big Data da PUC minas. Dispon�vel em: https://github.com/PatrickNogali/TCC-PUC-minas  
Em raz�o de seu tamanho e do limite imposto pelo GitHub (100 MB), o dataset "Acordaos2020" foi compactado e dividido em dois arquivos, "Acordaos2020.zip.001" e "Acordaos2020.zip.002" por meio do software livre 7-Zip, dispon�vel em https://www.7-zip.org/. O mesmo software deve ser utilizado para a reconstru��o do arquivo original, ap�s o download de suas partes.

b) "sumulas": 158 s�mulas do CARF vigentes em jul/2021, contendo n�mero da s�mula, enunciado e respectivos n�meros de ac�rd�os precedentes.  
Fonte: web scraping da p�gina "Quadro Geral de S�mulas" do CARF, alcan�ada a partir de https://carf.economia.gov.br/, menu esquerdo "Jurisprud�ncia", "S�mulas CARF", �S�mulas Consolidadas com os Ac�rd�os Precedentes�.

c) "precedentes": 405 ac�rd�os precedentes de s�mulas do CARF, contendo os campos n�mero do ac�rd�o, ementa, relat�rio, voto (relator) e voto vencedor (quando houver).  
Fonte: web scraping da p�gina de pesquisa de ac�rd�os do CARF, alcan�ada pelo menu esquerdo "Jurisprud�ncia", "Ac�rd�os CARF", "Pesquisa de Ac�rd�os", at� o download do arquivo PDF contendo o texto integral do ac�rd�o.

### Descri��o dos notebooks (Python 3.8):

#### _1_scraping_sumulas
Obter do s�tio do CARF a rela��o de s�mulas aprovadas e vigentes, seu enunciado e respectivos n�meros de ac�rd�os precedentes.

#### _2_scraping_acordaos
Dado um n�mero de ac�rd�o precedente de s�mula, originado do dataset "sumulas" criado pelo notebook _1_scraping_sumulas, baixar o respectivo arquivo PDF do s�tio do CARF.

#### _3_xml_precedentes
A partir de arquivos PDF baixados pelo notebook _2_scraping_acordaos, contendo o inteiro teor de ac�rd�os precedentes de s�mulas, obter o documento XML embutido no PDF (quando houver), extrair os dados de interesse do XML e gerar o dataset "precedentes".

#### _4_tratamento
A partir dos datasets "acordaos2020", "sumulas" e "precedentes", realizar as transforma��es e integra��es necess�rias para produzir o dataset "corpus", insumo para os modelos de busca por similaridade.

#### _5_exploracao
Analisar o dataset "corpus" criado no notebook _4_tratamento.

#### _6_metrica
Implementar o c�lculo de m�tricas para aferir o quanto as representa��es vetoriais de documentos, produzidas por um modelo treinado, refletem suas similaridades.

#### _7_treino_teste
Criar os datasets "treino" e "teste" a partir do dataset "corpus" gerado pelo notebook _4_tratamento.

#### _8_tf_idf
Ajustar o modelo BoW TF-IDF e aferir a qualidade de suas representa��es vetoriais.
(requer o notebook _6_metrica sob a mesma pasta deste)

#### _9_doc2vec
Treinar o modelo Doc2Vec e aferir a qualidade de suas representa��es vetoriais.
(requer o notebook _6_metrica sob a mesma pasta deste)
