# ICConv: A Large-Scale Intent-Oriented and Context-Aware Conversational Search Dataset
We constructed this dataset to relieve the data scarcity problem of conversational search to an extent. Data scarcity has been a problem hindering the research of conversational search. Due to the high cost of manual construction, some methods tried to build datasets automatically. However, existing methods for building conversational search datasets either overlook the multi-intent problem and contextual information or create a biased dataset where all queries in a conversation are related to a single positive passage. Considering the multi-intent problem and contextual information, we constructed this large-scale intent-oriented and context-aware dataset automatically based on the web search session data in [MS MARCO](https://microsoft.github.io/msmarco/).



## Download

```shell
git lfs install
git clone https://github.com/hongjx175/ICConv.git
cd ICConv
git lfs pull
```

## Meta

| **Statistics**          | **Train** | **Dev** | **Test** |
| ----------------------- | --------- | ------- | -------- |
| \# Conversation         | 84,704    | 10,589  | 10,588   |
| \# Query                | 585,129   | 73,371  | 73,569   |
| \# Answer               | 585,129   | 73,371  | 73,569   |
| \# Avg. Token / Conv    | 186.41    | 187.20  | 187.55   |
| \# Avg. Token / Query   | 5.50      | 5.50    | 5.51     |
| \# Avg. Token / Answer  | 21.78     | 21.81   | 21.77    |
| \# Avg. Token / Passage | 58.03     | 58.24   | 57.66    |



The data is in JSON format. The dataset contains three JSON files: `train_sessions.json`, `dev_sessions.json`, `test_sessions.json`. Each JSON file contains a list of JSON objects, where each JSON object represents a conversation. 

The following are the fields of JSON:

* `session_id (string) `: The unique identifier of the conversation reserved from MS MARCO.
* `turns (list of JSON objects) `: A list of the conversation turns. The fields in every turn are:
    * `qid (int)` : The original qid of the web search query used to convert in MS MARCO.
    * `query (string) `: The conversational natural language query.
    * `oracle_query (string) `: The natural language query, which is de-contextualized.
    * `answer (string)` : The response to the query we extracted from the positive passage.
    * `passage (int & string)` : The ID of the positive passage and its content. The passages are from MS MARCO passage V1.

## Citation

