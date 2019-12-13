![alt text](https://digitalexchange.blueprism.com/dpCatalogForm/renderFile/fe5c17a0-ff99-4f4c-bbe6-fc0792132f40 "DX Community Developer")

<!-- [Markdown Cheetsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links) -->

<!-- Asset Name -->
# Stanford CoreNLP Capability

<!-- Asset Pitch -->
A Blue Prism skill that implements the Web API interface to the [Stanford CoreNLP server](https://stanfordnlp.github.io/CoreNLP/ "Stanford CoreNLP wiki page").

### Whats Included:
+ Stanford CoreNLP Skill v1.0.bpskill - Blue Prism skill
+ Standford CoreNLP - Basic Actions v1.0.bprelease - A VBO to expose the Stanford CoreNLP Skill via Blue Prism actions. 
+ Standford CoreNLP - Example Process v1.0.bprelease - A sample process that uses the Stanford CoreNLP Skill and VBO for simple NLP tasks.

### Pre-Requisites
- Open JDK 8 or equivalent (64-bit preferred due to the VM memory requirements)
- Stanford CoreNLP 3.9.2

## Getting Started:

### Install the JDK:
- I installed [OpenJDK 8 (LTS)](https://adoptopenjdk.net)

#### Download the CoreNLP v3.9.2 package:
[Download](https://stanfordnlp.github.io/CoreNLP/index.html#download) and unzip it to the directory of you choice. 
- I installed it in ``` C:\BluePrism\Projects\Stanford\CoreNLP ``` but it should not matter since the VBO accesses the server API via the URL http://localhost:9000

#### Install the Blue Prism skill from the Digital Exchange:
- Install the **Stanford CoreNLP Skill v1.0.bpskill** to your Blue Prism database.

#### (OPTIONAL) Install the additional Blue Prism assets from the Digital Exchange:
- Install the **Standford CoreNLP - Basic Actions v1.0.bprelease** to your Blue Prism database.
- Install the **Standford CoreNLP - Example Process v1.0.bprelease** to your Blue Prism database.

#### Verifying your pre-requisite installs:
> NOTE: Once you have the JDK installed, the CoreNLP is unzipped and ready and the bprealease installed and ready type the following in a command window...

- In a command line window:
```bash
cd C:\BluePrism\Projects\Stanford\CoreNLP  // or the folder location where you unzipped the CoreNLP package
java -cp "*" -Xmx8g edu.stanford.nlp.pipeline.StanfordCoreNLPServer -annotators "tokenize" -preload "tokenize, ssplit, pos, parse, lemma, depparse" 
```
__Important Note:__
> If you run into issue starting the server you may need to check the JDK install, permissions or memory allocation.  Please refer to the Stamford CoreNLP

Once the server has started, using the browser of your choice and enter the following URLs to test if the server is alive and ready to take requests:
- http://localhost:9000/live - server started succesfully
- http://localhost:9000/ready - the default configurations are loaded and ready to take requests
