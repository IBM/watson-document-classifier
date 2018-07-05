This code pattern enables augmentation of the output from Watson Natural Language Understanding in certain scenarios:

** Extraction of domain specific entities
We wish to extract entities which are domain specific. Let us take the domain of computing as an example. `Snapdragon`, `Atom` or `Sandy Bridge` are names of processors. Such classifications are better achieved with a dictionary. When we do not already have a custom model for Watson Natural Language Understanding, this pattern reduces the effort with the help of a rules based configuration file.

** Conditional classification
A text can be classified in multiple ways. A 10 digit number can be a phone number or an order number depending on the context. The approach provided in this pattern can enable conditional classification after determining the context.

** Override classification from Watson Natural Language Understanding based on context
We can have scenarios where we might need to override the classifications from Watson Natural Language Understanding based on context. A Gorilla is usually classified as an animal but it needs to be classified as a type of glass in certain contexts. Without modifying the models, we can override the classification based on the context.

## Below are some usecases where this code pattern can be applied:

### Content recommendation
Based upon the news articles users visited, the news portal wants to present links to articles they may also like
