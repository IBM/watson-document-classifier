## 1. Applicable scenarios
This code pattern provides an approach to augment the output from Watson Natural Language Understanding. Some of the scenarios where this approach can be used are specified below:

- **Extraction of domain specific entities**

To understand what we mean by domain specific entities, let us take the domain of computing. `Snapdragon`, `Atom` or `Sandy Bridge` are names of processors. The names are very specific to the domain of computing. The requirement could be to extract entities which are domain specific, and in addition there could be no documents available for training an NLP tool. Such text classifications are better achieved with a dictionary. When we do not already have a custom model for Watson Natural Language Understanding or any documents for training, the approach specified in the pattern helps achieve the classification using a rules based configuration file. 

- **Conditional classification**

A text can be classified in multiple ways. A 10 digit number can be a phone number or an order number depending on the context. The approach provided in this pattern can enable conditional classification after determining the context.

- **Override classification from Watson Natural Language Understanding based on context**

We can have scenarios where we might need to override the classifications from Watson Natural Language Understanding based on context. A Gorilla is usually classified as an animal but it needs to be classified as a type of glass in certain contexts. Without modifying the models, we can override the classification based on the context using the approach specified in the pattern.

> Note: The code and configuration provided in this repository can be modified to build a solution for the above scenarios. 

## 2. Usecases 

### a. Content recommendation
Based upon the news articles users visited, the news portal wants to present links to articles they may also like
