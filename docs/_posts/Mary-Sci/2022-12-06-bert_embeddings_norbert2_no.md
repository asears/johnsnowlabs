---
layout: model
title: Norwegian BertForMaskedLM Cased model (from ltgoslo)
author: John Snow Labs
name: bert_embeddings_norbert2
date: 2022-12-06
tags: ["no", open_source, bert_embeddings, bertformaskedlm]
task: Embeddings
language: "no"
edition: Spark NLP 4.2.4
spark_version: 3.0
supported: true
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForMaskedLM model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `norbert2` is a Norwegian model originally trained by `ltgoslo`.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_embeddings_norbert2_no_4.2.4_3.0_1670327036179.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_embeddings_norbert2_no_4.2.4_3.0_1670327036179.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
documentAssembler = DocumentAssembler() \
    .setInputCols(["text"]) \
    .setOutputCols("document")

tokenizer = Tokenizer() \
    .setInputCols("document") \
    .setOutputCol("token")

bert_loaded = BertEmbeddings.pretrained("bert_embeddings_norbert2","no") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("embeddings") \
    .setCaseSensitive(True)
    
pipeline = Pipeline(stages=[documentAssembler, tokenizer, bert_loaded])

data = spark.createDataFrame([["I love Spark NLP"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler() 
    .setInputCols(Array("text")) 
    .setOutputCols(Array("document"))
      
val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")
 
val bert_loaded = BertEmbeddings.pretrained("bert_embeddings_norbert2","no") 
    .setInputCols(Array("document", "token"))
    .setOutputCol("embeddings")
    .setCaseSensitive(True)    
   
val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, bert_loaded))

val data = Seq("I love Spark NLP").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_embeddings_norbert2|
|Compatibility:|Spark NLP 4.2.4+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[sentence, token]|
|Output Labels:|[bert]|
|Language:|no|
|Size:|467.9 MB|
|Case sensitive:|true|

## References

- [https://huggingface.co/ltgoslo/norbert2](https://huggingface.co/ltgoslo/norbert2)
- [https://vectors.nlpl.eu/repository/20/221.zip](https://vectors.nlpl.eu/repository/20/221.zip)
- [https://norlm.nlpl.eu/](https://norlm.nlpl.eu/)
- [https://github.com/ltgoslo/NorBERT](https://github.com/ltgoslo/NorBERT)
- [https://aclanthology.org/2021.nodalida-main.4/](https://aclanthology.org/2021.nodalida-main.4/)
- [https://www.eosc-nordic.eu/](https://www.eosc-nordic.eu/)
- [https://www.mn.uio.no/ifi/english/research/groups/ltg/](https://www.mn.uio.no/ifi/english/research/groups/ltg/)