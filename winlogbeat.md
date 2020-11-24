Truncate everything in message after the first sentence, as this content is already parsed. Should reduce log size by ~50%
```
# ================================= Processors =================================
processors:
  - dissect:
    # Reference https://github.com/elastic/beats/issues/16591
      tokenizer: "%{message}."
      field: "message"
      target_prefix: ""
```
