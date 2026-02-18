# Configuration_example

## Hugging Face Dataset

|       Field       |  Type   |                                                          Description                                                           |                             Options                              |
|:-----------------:|:-------:|:------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------:|
|       name        | string  |                                          A short name for this configuration or task.                                          |                               Any                                |
|      dataset      | string  |                                                      The dataset source.                                                       |              Any dataset from hugging face datasets              |
|      version      | string  |                                            Version, split or subset of the dataset.                                            |                               Any                                |
|  backup_interval  | integer | Frequency  at which to save progress or checkpoints. A value of 5 means the system will back up after every 5 processed items. |                            Unlimited                             |
| columns2translate |  array  |                                     Specifies which dataset columns should be translated.                                      |                               Any                                |
|      col_id       | string  |                                      Name of the unique identifier column in the dataset                                       | Any, if the id doesn't exist it will assume the index as the id. |
|      reader       | string  |                                           Defines the type of dataset/file to read.                                            |                  "hugging_face" (in this case)                   |
|  source_language  | string  |                                        The original language code of the given dataset                                         |                  Depends on the choosen method                   |
|  target_language  | string  |                                              The target translation language code                                              |                  Depends on the choosen method                   |
|  backup_interval  | integer | Frequency  at which to save progress or checkpoints. A value of 5 means the system will back up after every 5 processed items. |                            Unlimited                             |

We need to choose the method we will use for translation, at the moment, we have two options:


| Field  |  Type  |                        Description                        | Options |
|:------:|:------:|:---------------------------------------------------------:|:-------:|
| method | string | Defines the method that will be used for the translation. | "deepL" |

or

|   Field    |  Type  |                                   Description                                    |       Options        |
|:----------:|:------:|:--------------------------------------------------------------------------------:|:--------------------:|
|   method   | string |            Defines the method that will be used for the translation.             |       "model"        |
|   model    | string | The translation model to be used. The model should support transformers pipeline |         Any          |
| max_tokens |  int   | Sets the maximum number of tokens the model can process per translation request. | Depends on the model |

Example:
```
{       
        "name": "bigbench",
        "dataset": "tasksource/bigbench",
        "version": "movie_recommendation",
        "backup_interval": 10,
        "columns2translate": ["inputs", "targets", "multiple_choice_targets"],
        "col_id":"idx",
        "reader":"hugging_face",
        "source_language": "en",
        "target_language": "pt-PT",
        "method": "model",
        "model": "rhaymison/opus-en-to-pt-translator", 
        "max_tokens":400
}
```

## CSV | JSON | JSONL | XML | TML 

|       Field       |  Type   |                                                          Description                                                           |                                       Options                                        |
|:-----------------:|:-------:|:------------------------------------------------------------------------------------------------------------------------------:|:------------------------------------------------------------------------------------:|
|       name        | string  |                                          A short name for this configuration or task.                                          |                                         Any                                          |
|   source_folder   | string  |                                             File folder that we want to translated                                             |                                         Any                                          |
|  backup_interval  | integer | Frequency  at which to save progress or checkpoints. A value of 5 means the system will back up after every 5 processed items. |                                      Unlimited                                       |
| columns2translate |  array  |                                     Specifies which dataset columns should be translated.                                      |                                         Any                                          |
|      col_id       | string  |                                      Name of the unique identifier column in the dataset                                       | Any, if this field doesn't exist it will assume the index as the id. <br> (Optional) |
|    split_name     | string  |                               Choose the name of the split that will show in the column "split"                                |                                         Any                                          |
|      reader       | string  |                                           Defines the type of dataset/file to read.                                            |                        "csv", "json", "jsonl", "xml" or "tml"                        |
|  source_language  | string  |                                        The original language code of the given dataset                                         |                            Depends on the choosen method                             |
|  target_language  | string  |                                              The target translation language code                                              |                            Depends on the choosen method                             |


                   
We need to choose the method we will use for translation, at the moment, we have two options:


| Field  |  Type  |                        Description                        | Options |
|:------:|:------:|:---------------------------------------------------------:|:-------:|
| method | string | Defines the method that will be used for the translation. | "deepL" |

or

|   Field    |  Type  |                                   Description                                    |       Options        |
|:----------:|:------:|:--------------------------------------------------------------------------------:|:--------------------:|
|   method   | string |            Defines the method that will be used for the translation.             |       "model"        |
|   model    | string | The translation model to be used. The model should support transformers pipeline |         Any          |
| max_tokens |  int   | Sets the maximum number of tokens the model can process per translation request. | Depends on the model |

Example:
```
{
    "name": "mc_task",
    "source_folder": "original/TruthfulQA",
    "backup_interval": 10,
    "columns2translate": ["Question", "Best Answer", "Correct Answers", "Incorrect Answers"],
    "split_name": "train",
    "reader": "csv",
    "source_language": "en",
    "target_language": "pt",
    "method": "deepL"
}
```

```
{
    "name": "databricks-dolly-15k",
    "source_folder": "original/databricks-dolly-15k",
    "backup_interval": 10,
    "columns2translate": ["instruction", "context", "response"],
    "split_name": "instruction",
    "reader": "jsonl",
    "source_language": "en",
    "target_language": "pt",
    "method": "model",
    "model": "rhaymison/opus-en-to-pt-translator",
    "max_tokens":400
}
```
