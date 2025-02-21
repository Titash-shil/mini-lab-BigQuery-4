# || [mini lab : BigQuery : 4](https://www.cloudskillsboost.google/catalog) || 

## # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

---
## ⚠️ **Disclaimer:**
#### This script and guide are provided for educational purposes to help you understand the lab process. Please ensure you understand the steps before using any scripts. Before using the script, I encourage you to open and review it to understand each step.The goal is to help you learn how to complete the labs effectively while following Qwiklabs' terms of service and YouTube's community guidelines.
---

### Run the following Commands in CloudShell

```
export PROJECT_ID=""
export DATASET_NAME=""
export TABLE_NAME=""
export BUCKET_NAME=""
export FILE_PATH="gs://BUCKET_NAME/products.csv"
```
- Run the below commands in shell - 1ST
```
bq load \
  --source_format=CSV \
  --autodetect \
  $PROJECT_ID:$DATASET_NAME.$TABLE_NAME \
  $FILE_PATH
```
- Run the below commands in shell - 2ND
```
bq query --use_legacy_sql=false "
CREATE SEARCH INDEX idx_product_search
ON \`$PROJECT_ID.$DATASET_NAME.$TABLE_NAME\`(SKU, name, orderedQuantity, stockLevel, restockingLeadTime);
"
```
- Run the below commands in shell - 3RD
```
bq query --use_legacy_sql=false "
CREATE SEARCH INDEX IF NOT EXISTS 
  \`$PROJECT_ID.$DATASET_NAME.products_information_search_index\`
ON \`$PROJECT_ID.$DATASET_NAME.products_information\` (ALL COLUMNS);
"
```
- Run the below commands in shell - 4TH
```
bq query --use_legacy_sql=false "
SELECT * 
FROM \`$PROJECT_ID.$DATASET_NAME.products_information\`
WHERE SEARCH(STRUCT(SKU, name, orderedQuantity, stockLevel, restockingLeadTime), '22 oz Water Bottle');
"
```
- # IF YOU GOT ERROR IN LAST COMMAND THEN ONLY RUN THIS COMMAND AGAIN
```
bq query --use_legacy_sql=false "
SELECT column_name
FROM \`$PROJECT_ID.$DATASET_NAME.INFORMATION_SCHEMA.COLUMNS\`
WHERE table_name = 'products_information';
"
```

---

## Congratulations ..!!🎉  You completed the lab shortly..😃💯

## *Well done..!* 👏

## Thank you for visiting.... :) 🗯️

## [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)

## Join to our community [Digital Dominators](https://chat.whatsapp.com/J0o1beFGCHfJ8ZHGKjcqkd)
