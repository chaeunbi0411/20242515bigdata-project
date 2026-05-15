LLM 정확도: 0.7700
LLM F1:    0.7579
분류 실패(Unknown): 0건

              precision    recall  f1-score   support

      Normal       0.84      0.73      0.78        56
   Anomalous       0.71      0.82      0.76        44

    accuracy                           0.77       100
   macro avg       0.77      0.78      0.77       100
weighted avg       0.78      0.77      0.77       100

PROMPT_TEMPLATE = '''
You are a web security expert.
Classify the HTTP request as either "Normal" or "Anomalous".

Rules:
- Normal: ordinary page access, login, search, product view, or form submission.
- Anomalous: SQL injection, XSS, path traversal, command injection.
- Respond only in JSON format.
- The label must be exactly "Normal" or "Anomalous".

Examples:

Request: GET /index.jsp HTTP/1.1
Output: {{"label": "Normal", "reason": "Ordinary page request"}}

Request: POST /login.jsp HTTP/1.1
Body: username=kim&password=1234
Output: {{"label": "Normal", "reason": "Typical login form submission"}}

Request: GET /search?q=' OR '1'='1 HTTP/1.1
Output: {{"label": "Anomalous", "reason": "SQL injection pattern"}}

Request: GET /product?id=<script>alert(1)</script> HTTP/1.1
Output: {{"label": "Anomalous", "reason": "XSS payload detected"}}

Now classify:
Request: {http_text}

Output:
'''