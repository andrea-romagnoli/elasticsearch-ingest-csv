# Elasticsearch csv Ingest Processor

This processor can parse CSV data and stores it as individual fields.
This filter can also parse data with any separator, not just commas.

## Usage


```
PUT _ingest/pipeline/opennlp-pipeline
{
  "description": "A pipeline to do whatever",
  "processors": [
    {
      "csv" : {
        "field" : "my_field",
        "columnes" : ["a", "b"]
      }
    }
  ]
}

PUT /my-index/my-type/1?pipeline_id=opennlp-pipeline
{
  "my_field" : "a_value,b_value"
}

GET /my-index/my-type/1
{
  "my_field" : "a_value,b_value"
  "a" : "a_value",
  "b" : "b_value"
}
```

## Configuration

| Parameter | Use | Required |
| --- | --- | --- |
| field   | Field name of where to read the content from | Yes |
| columns  | Define a list of column names. | Yes |
| quote_char | Define the character used to quote CSV fields. If this is not specified the default is a double quote ". | No |
| separator | Define the column separator value. If this is not specified, the default is a comma ,. | No |

## Setup

In order to install this plugin, you need to create a zip distribution first by running

```bash
gradle clean check
```

This will produce a zip file in `build/distributions`.

After building the zip file, you can install it like this

```bash
bin/plugin install file:///path/to/ingest-csv/build/distribution/ingest-csv-0.0.1-SNAPSHOT.zip
```

## Bugs & TODO

* Need more test, like using separator and quote_char 
* and todos...
