# ecommerce-review-analysis

This app analyzes customer-reviews for E-commerce products.

Data source: https://www.kaggle.com/datasets/cynthiarempel/amazon-us-customer-reviews-dataset?resource=download

## Usage

You need a Unix-compatible (macOS, Linux or Windows [WSL](https://learn.microsoft.com/en-us/windows/wsl/install))
system to run this app. Open a terminal and execute the steps below:

You need to specify the OpenAI API key as shown below.

```shell
export OPENAI_API_KEY="FIXME"
```

You may run this app without making a local copy first (i.e. clone the repo)
using Docker as follows:

```shell
docker run --rm \
  -p "0.0.0.0:8080:8080" \
  -v $PWD:/agentlang \
  -e OPENAI_API_KEY="$OPENAI_API_KEY" \
  -it agentlang/agentlang.cli:latest \
  agent clonerun https://github.com/agentlang-hub/ecommerce-review-analysis.git
```

### Running a local copy of the app

If you have cloned the app and made a local copy on your computer,
you may run it using Docker as follows:

```shell
docker run --rm \
  -p "0.0.0.0:8080:8080" \
  -v $PWD:/agentlang \
  -e OPENAI_API_KEY="$OPENAI_API_KEY" \
  -it agentlang/agentlang.cli:latest \
  agent run
```

Alternatively, instead of Docker you may use the locally installed
[Agentlang CLI](https://github.com/agentlang-ai/agentlang.cli):

```shell
agent run
```


### Post a customer review

In another terminal:

```shell
curl -X POST http://localhost:8080/api/EcommerceReviewAnalysis.Core/Review \
  -H 'Content-type: application/json' \
  --data-binary @sample.json
```

After the request is submitted successfully, you may inspect the analysis as follows:

```shell
curl http://localhost:8080/api/EcommerceReviewAnalysis.Core/Analysis
```

## License

Copyright 2024-2025 Fractl Inc.

Licensed under the Apache License, Version 2.0:
http://www.apache.org/licenses/LICENSE-2.0

