---
layout: model
title: English RobertaForSequenceClassification Cased model (from SkolkovoInstitute)
author: John Snow Labs
name: roberta_classifier_toxicity
date: 2022-09-09
tags: [en, open_source, roberta, sequence_classification, classification]
task: Text Classification
language: en
nav_key: models
edition: Spark NLP 4.1.0
spark_version: 3.0
supported: true
annotator: RoBertaForSequenceClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained RobertaForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `roberta_toxicity_classifier` is a English model originally trained by `SkolkovoInstitute`.

## Predicted Entities

`neutral`, `toxic`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/roberta_classifier_toxicity_en_4.1.0_3.0_1662767197642.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/roberta_classifier_toxicity_en_4.1.0_3.0_1662767197642.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

seq_classifier = RoBertaForSequenceClassification.pretrained("roberta_classifier_toxicity","en") \
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
 
val seq_classifier = RoBertaForSequenceClassification.pretrained("roberta_classifier_toxicity","en") 
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
|Model Name:|roberta_classifier_toxicity|
|Compatibility:|Spark NLP 4.1.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|en|
|Size:|468.6 MB|
|Case sensitive:|true|
|Max sentence length:|256|

## References

- [https://huggingface.co/SkolkovoInstitute/roberta_toxicity_classifier](https://huggingface.co/SkolkovoInstitute/roberta_toxicity_classifier)
- [https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge)
- [https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification)
- [https://www.kaggle.com/c/jigsaw-multilingual-toxic-comment-classification](https://www.kaggle.com/c/jigsaw-multilingual-toxic-comment-classification)
- [https://arxiv.org/abs/1907.11692](https://arxiv.org/abs/1907.11692)
- [https://creativecommons.org/licenses/by-nc-sa/4.0/](https://creativecommons.org/licenses/by-nc-sa/4.0/)