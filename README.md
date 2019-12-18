![alt text](https://digitalexchange.blueprism.com/dpCatalogForm/renderFile/fe5c17a0-ff99-4f4c-bbe6-fc0792132f40 "DX Community Developer")

<!-- [Markdown Cheetsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links) -->

<!-- Asset Name -->
## 1. Stanford CoreNLP Capability

<!-- Asset Pitch -->
A Blue Prism skill that implements the Web API interface to the [Stanford CoreNLP server](https://stanfordnlp.github.io/CoreNLP/ "Stanford CoreNLP wiki page").


### Whats Included:
+ Stanford CoreNLP Capability Skill.bpskill - Blue Prism skill
+ Standford CoreNLP - Basic Actions v1.0.bprelease - A VBO to expose the Stanford CoreNLP Skill via Blue Prism actions. 
+ Standford CoreNLP - Example Process v1.0.bprelease - A sample process that uses the Stanford CoreNLP Skill and VBO for simple NLP tasks.

#### Documentation
+ Blue_Prism_Stanford_CoreNLP_Capability_Skill_User_Guide.pdf

### Pre-Requisites
- Open JDK 8 or equivalent (64-bit preferred due to the VM memory requirements)
- Stanford CoreNLP 3.9.2

## 2. Getting Started:

- Install the JDK:
  - I installed [OpenJDK 8 (LTS)](https://adoptopenjdk.net)
  
- Download the [CoreNLP v3.9.2 package](https://stanfordnlp.github.io/CoreNLP/index.html#download) and unzip it to the directory of you choice. 
  - I installed it in ``` C:\BluePrism\Projects\Stanford\CoreNLP ``` but it should not matter since the VBO accesses the server API via the URL http://localhost:9000

- Install the Blue Prism skill from the Digital Exchange:
  - Install the **Stanford CoreNLP Skill v1.0.bpskill** to your Blue Prism database.

- Optionally install the additional Blue Prism assets from the Digital Exchange:
  - Install the **Standford CoreNLP - Basic Actions v1.0.bprelease** to your Blue Prism database.
  - Install the **Standford CoreNLP - Example Process v1.0.bprelease** to your Blue Prism database.

### 2.1 Verifying the CoreNLP Server:
> NOTE: Once you have the JDK installed, the CoreNLP is unzipped and ready and the bprealease installed and ready type the following in a command window...

- To start the server, open a command line window or use a batch file to execute the following commands:
```bash
cd <Enter Your CoreNLP install Location here >
java -cp "*" -Xmx8g edu.stanford.nlp.pipeline.StanfordCoreNLPServer -annotators "tokenize" -preload "tokenize, ssplit, pos, parse, lemma, depparse" 
```
Once the server has started, using the browser of your choice and enter the following URLs to test if the server is alive and ready to take requests:
- http://localhost:9000/live - server started succesfully
- http://localhost:9000/ready - the default configurations are loaded and ready to take requests

If this all goes well you should be able to run the provided __Standford CoreNLP - Example Process v1.0.bprelease__ with the __Standford CoreNLP - Basic Actions v1.0.bprelease__.

For more detailed information on how to use the Stanford CoreNLP API please visit:
- [Stamford CoreNLP](https://stanfordnlp.github.io/CoreNLP)
- [Stamford CoreNLP FAQ](https://stanfordnlp.github.io/CoreNLP/faq.html)

:heavy_exclamation_mark: Important Note: Once the CoreNLP server is setup correctly it runs very well. If for some reason you run into issues starting the server or with slow performance please refer to the following sections for help:
- [CoreNLP Server](https://stanfordnlp.github.io/CoreNLP/corenlp-server.html)
- [Understanding memory and time usage](https://stanfordnlp.github.io/CoreNLP/memory-time.html)

## 3. Using the Skill
> There is essentially two ways to use the Stanford CoreNLP API in Blue Prism.
- Using the [skill](#using-the-skill) directly
- Using and modifying the additional [VBO](#using_the_VBO) asset.

Below is a list of available actions from the Web API:

### 3.1 Using the Skill

---
### Annotate:
> This is the general action to annotate text using one of the provided "annotators" included in the Stanford CoreNLP API.  
[Complete Annotator Listing](https://stanfordnlp.github.io/CoreNLP/annotators.html)

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
properties|Text|Y|The properties JSON string to pass to the CoreNLP server.
text|Text|Y|The text to apply the annotators list.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Response_Content|Text|A JSON value containing response information related to the request.
HTTP Status Code|Text|HTTP Status code returned in response.
Response Headers|Collection|Collection of headers data returned in response.
&nbsp;

---
### TokenRegex:
> A simple, rule-based NER over token sequences using Java regular expressions..  This can also be run as an annotator using Annotate action with the annotator 'tokensregex'

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
pattern|Text|Y| The TokensRegex pattern to annotate.
properties|Text|Y| The properties JSON string to pass to the CoreNLP server
text|Text|Y|The text to apply the annotators list.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Response_Content|Text|A JSON value containing response information related to the request.
HTTP Status Code|Text|HTTP Status code returned in response.
Response Headers|Collection|Collection of headers data returned in response.
&nbsp;

---
### Semgrex:
> An implementation of the SemgrexPattern pattern for matching node and edge configurations of a dependency graph.

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
pattern|Text|Y|The Semgrex pattern to annotate.
properties|Text|Y|If true, entire sentences must match the pattern, rather than the API finding matching sections.
text|Text|Y|The text to apply the annotators list.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Response_Content|Text|A JSON value containing response information related to the request.
HTTP Status Code|Text|HTTP Status code returned in response.
Response Headers|Collection|Collection of headers data returned in response.
&nbsp;

---
### Tregex:
> A utility for matching patterns in trees, based on tree relationships and regular expression matches on nodes (the name is short for "tree regular expressions")

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
pattern|Text|Y|The Tregex pattern to annotate.
properties|Text|Y|The properties JSON string to pass to the CoreNLP server
text|Text|Y|The text to apply the annotators list.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Response_Content|Text|A JSON value containing response information related to the request.
HTTP Status Code|Text|HTTP Status code returned in response.
Response Headers|Collection|Collection of headers data returned in response.
&nbsp;

---
### Live: 
> Check server liveness - is online

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
none|||
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Response_Content|Text|A JSON value containing response information related to the request.
HTTP Status Code|Text|HTTP Status code returned in response.
Response Headers|Collection|Collection of headers data returned in response.
&nbsp;

---
### Ready:
> Check server readiness - annotators are loaded and the server is ready to accept connections

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
none|||
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Response_Content|Text|A JSON value containing response information related to the request.
HTTP Status Code|Text|HTTP Status code returned in response.
Response Headers|Collection|Collection of headers data returned in response.

# 3.2 Using the VBO
> The __Standford CoreNLP - Basic Actions VBO__ is an additional asset that makes the usage of the Stamford CoreNLP API a little more Blue Prism process friendly.  It includes all the same functionality of the Skill but with some added encapsulation, basic error handling. The VBO additionally calls the (/ready) action to verify the server is ready before each request so that the user can more appropriately handle retries and connection issues.

Below is a list of available actions from the __Standford CoreNLP - Basic Actions VBO__:

### Annotate Text:
> This is the general action to annotate text using one of the provided "annotators" included in the Stanford CoreNLP API.  

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
Options|Collection|Y|The collection of (Key=Value) pairs that represent the properties to pass to the CoreNLP server. 
Text|Text|Y|The text to apply the annotators list.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
JSON|Text|A JSON value containing response information related to the request.
Collection|Collection|A JSON value containing response information related to the request.
Status|Text|HTTP Status code returned in response.
Message|Text|Status Message returned by the request.
&nbsp;

---
### TokenRegex:
> A simple, rule-based NER over token sequences using Java regular expressions..  This can also be run as an annotator using Annotate action with the annotator 'tokensregex'

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
Options|Collection|Y|The collection of (Key=Value) pairs that represent the properties to pass to the CoreNLP server. 
Text|Text|Y|The text to apply the annotators list.
Pattern|Text|Y| The TokensRegex pattern to annotate.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
JSON|Text|A JSON value containing response information related to the request.
Collection|Collection|A JSON value containing response information related to the request.
Status|Text|HTTP Status code returned in response.
Message|Text|Status Message returned by the request.
&nbsp;

---
### Semgrex:
> An implementation of the SemgrexPattern pattern for matching node and edge configurations of a dependency graph.

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
Options|Collection|Y|The collection of (Key=Value) pairs that represent the properties to pass to the CoreNLP server. 
Text|Text|Y|The text to apply the annotators list.
Pattern|Text|Y| The TokensRegex pattern to annotate.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
JSON|Text|A JSON value containing response information related to the request.
Collection|Collection|A JSON value containing response information related to the request.
Status|Text|HTTP Status code returned in response.
Message|Text|Status Message returned by the request.
&nbsp;

---
### Tregex:
> A utility for matching patterns in trees, based on tree relationships and regular expression matches on nodes (the name is short for "tree regular expressions")

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
Options|Collection|Y|The collection of (Key=Value) pairs that represent the properties to pass to the CoreNLP server. 
Text|Text|Y|The text to apply the annotators list.
Pattern|Text|Y| The TokensRegex pattern to annotate.
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
JSON|Text|A JSON value containing response information related to the request.
Collection|Collection|A JSON value containing response information related to the request.
Status|Text|HTTP Status code returned in response.
Message|Text|Status Message returned by the request.
---
&nbsp;

---
### Live: 
> Check server liveness - is online

Input Parameter | Type | Required | Description
------------  | ------------- | ------------- | -------------
none |||
&nbsp;

Output Parameter | Type | Description
------------  | ------------- | -------------
Live|Boolean|The status of the server (online)
&nbsp;
