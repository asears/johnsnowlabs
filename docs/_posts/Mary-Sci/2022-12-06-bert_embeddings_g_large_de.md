---
layout: model
title: German BertForMaskedLM Large Cased model (from deepset)
author: John Snow Labs
name: bert_embeddings_g_large
date: 2022-12-06
tags: [de, open_source, bert_embeddings, bertformaskedlm]
task: Embeddings
language: de
edition: Spark NLP 4.2.4
spark_version: 3.0
supported: true
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForMaskedLM model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `gbert-large` is a German model originally trained by `deepset`.

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_embeddings_g_large_de_4.2.4_3.0_1670326448640.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_embeddings_g_large_de_4.2.4_3.0_1670326448640.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

bert_loaded = BertEmbeddings.pretrained("bert_embeddings_g_large","de") \
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
 
val bert_loaded = BertEmbeddings.pretrained("bert_embeddings_g_large","de") 
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
|Model Name:|bert_embeddings_g_large|
|Compatibility:|Spark NLP 4.2.4+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[sentence, token]|
|Output Labels:|[bert]|
|Language:|de|
|Size:|1.3 GB|
|Case sensitive:|true|

## References

- [https://huggingface.co/deepset/gbert-large](https://huggingface.co/deepset/gbert-large)
- [https://arxiv.org/pdf/2010.10906.pdf](https://arxiv.org/pdf/2010.10906.pdf)
- [https://arxiv.org/pdf/2010.10906.pdf](https://arxiv.org/pdf/2010.10906.pdf)
- [https://deepset.ai/](https://deepset.ai/)
- [https://haystack.deepset.ai/](https://haystack.deepset.ai/)
- [https://deepset.ai/german-bert](https://deepset.ai/german-bert)
- [https://deepset.ai/germanquad](https://deepset.ai/germanquad)
- [https://github.com/deepset-ai/haystack](https://github.com/deepset-ai/haystack)
- [https://docs.haystack.deepset.ai](https://docs.haystack.deepset.ai)
- [https://haystack.deepset.ai/community](https://haystack.deepset.ai/community)
- [https://twitter.com/deepset_ai](https://twitter.com/deepset_ai)
- [https://www.linkedin.com/company/deepset-ai/](https://www.linkedin.com/company/deepset-ai/)
- [https://haystack.deepset.ai/community](https://haystack.deepset.ai/community)
- [https://github.com/deepset-ai/haystack/discussions](https://github.com/deepset-ai/haystack/discussions)
- [https://deepset.ai](https://deepset.ai)
- [https://www.deepset.ai/jobs](https://www.deepset.ai/jobs)