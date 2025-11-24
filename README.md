# spring-ai-toon-demo
Token-Oriented Object Notation (TOON) – Compact, human-readable, schema-aware JSON for LLM prompts.

Token-Oriented Object Notation is a compact, human-readable encoding of the JSON data model that minimizes tokens and makes structure easy for models to follow. It's intended for LLM input as a drop-in, lossless representation of your existing JSON.

TOON combines YAML's indentation-based structure for nested objects with a CSV-style tabular layout for uniform arrays. TOON's sweet spot is uniform arrays of objects (multiple fields per row, same structure across items), achieving CSV-like compactness while adding explicit structure that helps LLMs parse and validate data reliably. For deeply nested or non-uniform data, JSON may be more efficient.

The similarity to CSV is intentional: CSV is simple and ubiquitous, and TOON aims to keep that familiarity while remaining a lossless, drop-in representation of JSON for Large Language Models.

Think of it as a translation layer: use JSON programmatically, and encode it as TOON for LLM input.

![](https://raw.githubusercontent.com/AadityaUoHyd/spring-ai-toon-demo/refs/heads/main/images/toon.png)

## Compare formats (json, toon, yml, csv, xml)
https://toontools.vercel.app/playground

## Convert JSON to TOON format
https://jsonviewer.tools/converter/json-to-toon

## How to run project

### In case you have installed ollama locally, you don't need docker. Run this LLM before running springboot program.
I have locally installed ollama with llama3.2 model as its free, so I don't need docker. 
Otherwise, use docker-compose.yml file. you can use other LLM like ChatGPT as well, configure accordingly.
```
  C:\Users\abcha> ollama list
  NAME                        ID              SIZE      MODIFIED
  gemma3:1b                   8648f39daa8f    815 MB    5 minutes ago
  llama3.2:latest             a80c4f17acd5    2.0 GB    4 months ago
  mxbai-embed-large:latest    468836162de7    669 MB    8 months ago
  deepseek-r1:8b              28f8fd6cdc67    4.9 GB    9 months ago
  
  C:\Users\abcha> ollama run llama3.2:latest
  >>> Send a message (/? for help)
```

### After running project hit swagger url
http://localhost:8080/swagger-ui/index.html#/json-toon-demo-controller/compareJsonVsToon
Try it out -> execute

### Output at console
Will show token differences between json and toon.
```
2025-11-24T23:23:18.382+05:30  INFO 14344 --- [spring-ai-toon-demo] [nio-8080-exec-6] o.a.controller.JsonToonDemoController    : JSON Payload: {
"name" : "Aaditya Raj",
"age" : 32,
"country" : "India",
"skills" : [ "Spring Boot", "Databases", "Microservices", "DSA", "Kafka", "ReactJs", "Kubernetes" ],
"address" : {
"street" : "Banjara Hills Road",
"city" : "Hyderabad",
"zip" : "500034"
}
}
2025-11-24T23:23:18.397+05:30  INFO 14344 --- [spring-ai-toon-demo] [nio-8080-exec-6] o.a.controller.JsonToonDemoController    : TOON Payload: name: Aaditya Raj
age: 32
country: India
skills[7]: Spring Boot,Databases,Microservices,DSA,Kafka,ReactJs,Kubernetes
address:
street: Banjara Hills Road
city: Hyderabad
zip: "500034"
2025-11-24T23:23:18.414+05:30  INFO 14344 --- [spring-ai-toon-demo] [nio-8080-exec-6] o.a.controller.JsonToonDemoController    : JSON Input Tokens: 102
2025-11-24T23:23:18.414+05:30  INFO 14344 --- [spring-ai-toon-demo] [nio-8080-exec-6] o.a.controller.JsonToonDemoController    : TOON Input Tokens: 60
```
- Output at swagger
![](https://raw.githubusercontent.com/AadityaUoHyd/spring-ai-toon-demo/refs/heads/main/images/output.png)

## Sources
https://github.com/toon-format/toon

## LICENSE
https://github.com/AadityaUoHyd/spring-ai-toon-demo/blob/master/LICENSE