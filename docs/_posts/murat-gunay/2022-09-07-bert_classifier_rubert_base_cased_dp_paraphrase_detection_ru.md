---
layout: model
title: Russian BertForSequenceClassification Base Cased model (from cointegrated)
author: John Snow Labs
name: bert_classifier_rubert_base_cased_dp_paraphrase_detection
date: 2022-09-07
tags: [ru, open_source, bert, sequence_classification, classification]
task: Text Classification
language: ru
edition: Spark NLP 4.1.0
spark_version: 3.0
supported: true
annotator: BertForSequenceClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `rubert-base-cased-dp-paraphrase-detection` is a Russian model originally trained by `cointegrated`.

## Predicted Entities

`entailment`, `not_entailment`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_classifier_rubert_base_cased_dp_paraphrase_detection_ru_4.1.0_3.0_1662515095542.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_classifier_rubert_base_cased_dp_paraphrase_detection_ru_4.1.0_3.0_1662515095542.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

seq_classifier = BertForSequenceClassification.pretrained("bert_classifier_rubert_base_cased_dp_paraphrase_detection","ru") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("class")
    
pipeline = Pipeline(stages=[documentAssembler, tokenizer, seq_classifier])

data = spark.createDataFrame([["PUT YOUR STRING HERE"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler() 
      .setInputCols(Array("text")) 
      .setOutputCols(Array("document"))
      
val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")
 
val seq_classifier = BertForSequenceClassification.pretrained("bert_classifier_rubert_base_cased_dp_paraphrase_detection","ru") 
    .setInputCols(Array("document", "token")) 
    .setOutputCol("class")
   
val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, seq_classifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_classifier_rubert_base_cased_dp_paraphrase_detection|
|Compatibility:|Spark NLP 4.1.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|ru|
|Size:|667.2 MB|
|Case sensitive:|true|
|Max sentence length:|256|

## References

- [https://huggingface.co/cointegrated/rubert-base-cased-dp-paraphrase-detection](https://huggingface.co/cointegrated/rubert-base-cased-dp-paraphrase-detection)
- [https://docs.deeppavlov.ai/en/master/features/overview.html#ranking-model-docs](https://docs.deeppavlov.ai/en/master/features/overview.html#ranking-model-docs)
- [https://paraphraser.ru/](https://paraphraser.ru/)