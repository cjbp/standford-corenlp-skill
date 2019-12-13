![alt text](https://digitalexchange.blueprism.com/dpCatalogForm/renderFile/fe5c17a0-ff99-4f4c-bbe6-fc0792132f40 "DX Community Developer")

<!-- [Markdown Cheetsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links) -->

<!-- Asset Name -->
# Stanford CoreNLP Capability

<!-- Asset Pitch -->
A Blue Prism skill that implements the Web API interface to the [Stanford CoreNLP server](https://stanfordnlp.github.io/CoreNLP/ "Stanford CoreNLP wiki page").

Whats Included:
+ Stanford CoreNLP Skill v1.0.bpskill - Blue Prism skill
+ Standford CoreNLP - Basic Actions v1.0.bprelease - A VBO to expose the Stanford CoreNLP Skill via Blue Prism actions. 
+ Standford CoreNLP - Example Process v1.0.bprelease - A sample process that uses the Stanford CoreNLP Skill and VBO for simple NLP tasks.

### Pre-Requisites

	- Open JDK 8 or equivalent (64-bit preferred due to the VM memory requirements)
	- Stanford CoreNLP 3.9.2

#### Install the JDK

1. install your JDK - I installed [OpenJDK 8 (LTS)](https://adoptopenjdk.net)

2. Download the CoreNLP v3.9.2 from https://stanfordnlp.github.io/CoreNLP/index.html#download and unzip it to the directory of you liking.
I installed it in C:\BluePrism\Projects\Stanford\CoreNLP but it should not matter since the VBO accesses the server API via http://localhost:9000

Install the Stanford CoreNLP - Basic Actions v0.1 Draft.bprelease to your Blue Prism database.

 	It should contain the following:

		Processes
		   Skills
			Stanford Core NLP
                   		Stanford Core NLP - Test Process ( A Short example of how to use the VBO )

		Business Objects
		   Skills
			Stanford Core NLP
                               	   Stanford Core NLP - Basic Actions ( The VBO with access to the CoreNLP tools and Annotators )
		Web APIs
		   Stanford Core NLP

Once you have the JDK installed, the CoreNLP is unzipped and ready and the bprealease installed and ready type the following in a command window...

	cd C:\BluePrism\Projects\Stanford\CoreNLP   **note: or the location of your CoreNLP folder.

	java -cp "*" -mx4g edu.stanford.nlp.pipeline.StanfordCoreNLPServer **note: the -mx4g can be reduced or increased based on the needs of the annotator(s)

Use a browser and enter the following to test if the server is alive and ready to take requests:
	http://localhost:9000/live - server started succesfully
	http://localhost:9000/ready - the default configurations are loaded and ready to take requests

If this all works you should be able to run the provided Test Process to test the Stanford Core NLP - Basic Actions VBO.
I setup a few debug items for both positive and negative sentiment analysis so if you set either one of these Calc stages to the "Set Current Stage" and run the process you should see the results.

Have Fun!!!


