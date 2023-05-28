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

This is an example of conversation:

```json
{
    "session_id": "marco-gen-dev-761127",
    "turns": [
        {
            "qid": 566556,
            "query": "What are the symptoms of bronchitis?",
            "oracle_query": "What are the symptoms of bronchitis?",
            "answer": "Symptoms of bronchitis include coughing up yellow-grey mucus, sore throat, wheezing and having a blocked nose.",
            "passage": [
                1511891,
                "Cold & flu health centre. Bronchitis. Bronchitis is a common infection causing inflammation and irritation to the main airways of the lungs. Symptoms of bronchitis include coughing up yellow-grey mucus, sore throat, wheezing and having a blocked nose. Acute bronchitis may be responsible for the hacking cough and phlegm production that sometimes accompany an upper respiratory infection. In most cases, the infection is viral in origin, but sometimes it's caused by bacteria."
            ]
        },
        {
            "qid": 784788,
            "query": "What is pneumonia?",
            "oracle_query": "What is pneumonia?",
            "answer": "Pneumonia (nu-MO-ne-ah) is an infection in one or both of the lungs.",
            "passage": [
                1011041,
                "Pneumonia (nu-MO-ne-ah) is an infection in one or both of the lungs. Many germs\u00e2\u0080\u0094such as bacteria, viruses, and fungi\u00e2\u0080\u0094can cause pneumonia.The infection inflames your lungs' air sacs, which are called alveoli (al-VEE-uhl-eye).neumonia (nu-MO-ne-ah) is an infection in one or both of the lungs. Many germs\u00e2\u0080\u0094such as bacteria, viruses, and fungi\u00e2\u0080\u0094can cause pneumonia."
            ]
        },
        {
            "qid": 476203,
            "query": "What are its symptoms?",
            "oracle_query": "What are pneumonia's symptoms?",
            "answer": "Symptoms also can vary, depending on whether your pneumonia is bacterial or viral.",
            "passage": [
                385922,
                "Symptoms also can vary, depending on whether your pneumonia is bacterial or viral. 1  In bacterial pneumonia, your temperature may rise as high as 105 degrees F. 2  The initial symptoms of viral pneumonia are the same as influenza symptoms: fever, a dry cough, headache, muscle pain, and weakness."
            ]
        },
        {
            "qid": 508239,
            "query": "What are the symptoms of mono in adults?",
            "oracle_query": "What are the symptoms of mono in adults?",
            "answer": "2  The symptoms of mono include: 3  fever, 4  fatigue, 5  sore throat, and.",
            "passage": [
                1184563,
                "1 Most adults have laboratory evidence (antibodies against the EBV) indicative of a previous infection with EBV and are immune to further infection. 2  The symptoms of mono include: 3  fever, 4  fatigue, 5  sore throat, and. 6  swollen lymph nodes. 7  The diagnosis of mono is confirmed by blood tests."
            ]
        },
        {
            "qid": 507997,
            "query": "What about an inner ear infection?",
            "oracle_query": "What are the symptoms of an inner ear infection?",
            "answer": "Symptoms include dizziness, loss of balance, nausea, vomiting, tinnitus, and vertigo.",
            "passage": [
                1150712,
                "Labyrinthitis is an inner ear disorder. It occurs when a vestibular nerve, important to spatial navigation and balance control, becomes inflamed. Symptoms include dizziness, loss of balance, nausea, vomiting, tinnitus, and vertigo. With proper treatment, most people find relief from symptoms within 1 to 3 weeks."
            ]
        }
    ]
}
```

