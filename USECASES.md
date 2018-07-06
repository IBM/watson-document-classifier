## 1. Other business scenarios that this approach can help build a solution 
This code pattern provides an approach to augment the output from Watson Natural Language Understanding. Some of the scenarios where this approach can be used are specified below:

- **Extraction of domain specific entities**

To understand what we mean by domain specific entities, let us take the domain of computing. `Snapdragon`, `Atom` or `Sandy Bridge` are names of processors. The names are very specific to the domain of computing. The requirement could be to extract entities which are domain specific. In addition there could be no documents available for training an NLP tool. Such text classifications are better achieved with a dictionary. When we do not already have a custom model for Watson Natural Language Understanding or any documents for training, the approach specified in the pattern helps achieve the classification using a rules based configuration file. 

- **Conditional classification**

A text can be classified in multiple ways. A 10 digit number can be a phone number or an order number depending on the context. The approach provided in this pattern can enable conditional classification after determining the context.

- **Override classification from Watson Natural Language Understanding based on context**

We can have scenarios where we might need to override the classifications from Watson Natural Language Understanding based on context. A Gorilla is usually classified as an animal but it needs to be classified as a type of glass in certain contexts. Without modifying the models, we can override the classification based on the context using the approach specified in the pattern.

> Note: The code and configuration provided in this repository can be modified to build a solution for the above scenarios. 

## 2. Other Usecases that this approach can help build a solution

### I. Content recommendation
Based upon the previous reading history, the news portal wants to recommend articles to users. This can be done by classifying the text in every article of the news portal into pre-defined categories like Business, Food, Health etc. based on a dictionary. An article is assigned categories based on the text content. Based on the frequently read categories of the articles, the news portal can recommend articles belonging to those categories.

### II. Optimize Ads
M&E company wants to place advertisements on appropriate web pages to generate maximum clicks. For example - If there a smart phone ad, it must be displayed when a web page related to mobiles is being viewed. The text content on web pages can be classified and assigned categories. The advertisements too are classified into categories. For a web page belonging to certain categories, the ads belonging to the same categories can be displayed.

### III. Email classification
An Insurance, Telco or any other company recieve thousands of emails from customers. There is a need to understand key concepts within emails received from end client so that they can be classified and assigned priorities to take appropriate actions. 

### IV. Developing a Chatbot
A chat bot is used many times to collect information from end customers. The important facts in the response from end customers must be extracted so that it can be used for further processing. The end customer can provide a mobile number or Order id based on a request by the bot. Both are say 10 digit numbers. Now, we can classify the number as a mobile number or order id based on previous question from the chatbot.

> Note: The code and configuration provided in this repository can be modified to build a solution for the above usecases.
