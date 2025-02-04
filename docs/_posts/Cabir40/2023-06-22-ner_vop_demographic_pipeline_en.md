---
layout: model
title: NER Pipeline for Demographic Information - Voice of the Patient
author: John Snow Labs
name: ner_vop_demographic_pipeline
date: 2023-06-22
tags: [licensed, ner, pipeline, vop, en, demographic]
task: Named Entity Recognition
language: en
edition: Healthcare NLP 4.4.4
spark_version: 3.2
supported: true
annotator: PipelineModel
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

This pipeline extracts mentions of demographic information from health-related text in colloquial language.

## Predicted Entities



{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/clinical/models/ner_vop_demographic_pipeline_en_4.4.4_3.2_1687434586225.zip){:.button.button-orange.button-orange-trans.arr.button-icon.hidden}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/clinical/models/ner_vop_demographic_pipeline_en_4.4.4_3.2_1687434586225.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use

<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
from sparknlp.pretrained import PretrainedPipeline

pipeline = PretrainedPipeline("ner_vop_demographic_pipeline", "en", "clinical/models")

pipeline.annotate("
My grandma, who's 85 and Black, just had a pacemaker implanted in the cardiology department. The doctors say it'll help regulate her heartbeat and prevent future complications.
")

```
```scala
import com.johnsnowlabs.nlp.pretrained.PretrainedPipeline

val pipeline = new PretrainedPipeline("ner_vop_demographic_pipeline", "en", "clinical/models")

val result = pipeline.annotate("
My grandma, who's 85 and Black, just had a pacemaker implanted in the cardiology department. The doctors say it'll help regulate her heartbeat and prevent future complications.
")
```
</div>

<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
from sparknlp.pretrained import PretrainedPipeline

pipeline = PretrainedPipeline("ner_vop_demographic_pipeline", "en", "clinical/models")

pipeline.annotate("
My grandma, who's 85 and Black, just had a pacemaker implanted in the cardiology department. The doctors say it'll help regulate her heartbeat and prevent future complications.
")
```
```scala
import com.johnsnowlabs.nlp.pretrained.PretrainedPipeline

val pipeline = new PretrainedPipeline("ner_vop_demographic_pipeline", "en", "clinical/models")

val result = pipeline.annotate("
My grandma, who's 85 and Black, just had a pacemaker implanted in the cardiology department. The doctors say it'll help regulate her heartbeat and prevent future complications.
")
```
</div>

## Results

```bash
Results


| chunk   | ner_label     |
|:--------|:--------------|
| grandma | Gender        |
| 85      | Age           |
| Black   | RaceEthnicity |
| doctors | Employment    |
| her     | Gender        |


{:.model-param}
```

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|ner_vop_demographic_pipeline|
|Type:|pipeline|
|Compatibility:|Healthcare NLP 4.4.4+|
|License:|Licensed|
|Edition:|Official|
|Language:|en|
|Size:|791.6 MB|

## Included Models

- DocumentAssembler
- SentenceDetectorDLModel
- TokenizerModel
- WordEmbeddingsModel
- MedicalNerModel
- NerConverter