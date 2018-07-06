# Augmented Classification of text with Watson Natural Language Understanding and IBM Data Science experience

*Read this in other languages: [한국어](README-ko.md).*

> Data Science Experience is now Watson Studio. Although some images in this code pattern may show the service as Data Science Experience, the steps and processes will still work.

In this code pattern we will use Jupyter notebooks in Watson Studio to augment IBM Watson Natural Language Understanding API output through configurable mechanism for text classification.

When the reader has completed this code pattern, they will understand how to:

* Create and run a Jupyter notebook in Watson Studio.
* Use Object Storage to access data and configuration files.
* Use IBM Watson Natural Language Understanding API to extract metadata from documents in Jupyter notebooks.
* Extract and format unstructured data using simplified Python functions.
* Use a configuration file to build configurable and layered classification grammar.
* Use the combination of grammatical classification and regex patterns from a configuration file to classify word token classes.
* Store the processed output JSON in Object Storage.

The intended audience for this code pattern is developers who want to learn a method for augmenting classification metadata obtained from Watson Natural Language Understanding API, in situations when there is a scarcity of historical data. The traditional approach of training a Text Analytics model yields less than expected results. The distinguishing factor of this code pattern is that it allows a configurable mechanism of text classification. It helps give a developer a head start in the case of text from a specialized domain, with no generally available English parser.

![](doc/source/images/architecture.png)

## Included components

* [IBM Watson Studio](https://www.ibm.com/cloud/watson-studio): Analyze data using RStudio, Jupyter, and Python in a configured, collaborative environment that includes IBM value-adds, such as managed Spark.

* [IBM Cloud Object Storage](https://console.bluemix.net/catalog/infrastructure/cloud-object-storage): An IBM Cloud service that provides an unstructured cloud data store to build and deliver cost effective apps and services with high reliability and fast speed to market.

* [Watson Natural Language Understanding](https://console.bluemix.net/catalog/services/natural-language-understanding/?cm_sp=dw-bluemix-_-code-_-devcenter): A IBM Cloud service that can analyze text to extract meta-data from content such as concepts, entities, keywords, categories, sentiment, emotion, relations, semantic roles, using natural language understanding.

## Featured technologies

* [Jupyter Notebooks](http://jupyter.org/): An open-source web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.


# Watch the Video

[![](http://img.youtube.com/vi/kp8dcM9AKrA/0.jpg)](https://www.youtube.com/watch?v=kp8dcM9AKrA)

# Steps

Follow these steps to setup and run this code pattern. The steps are
described in detail below.

1. [Sign up for Watson Studio](#1-sign-up-for-watson-studio)
1. [Create IBM Cloud services](#2-create-ibm-cloud-services)
1. [Create the notebook](#3-create-the-notebook)
1. [Add the data and configuraton file](#4-add-the-data-and-configuration-file)
1. [Update the notebook with service credentials](#5-update-the-notebook-with-service-credentials)
1. [Run the notebook](#6-run-the-notebook)
1. [Download the results](#7-download-the-results)
1. [Analyze the results](#8-analyze-the-results)

## 1. Sign up for Watson Studio

Sign up for IBM's [Watson Studio](https://dataplatform.ibm.com). By creating a project in Watson Studio a free tier ``Object Storage`` service will be created in your IBM Cloud account. Take note of your service names as you will need to select them in the following steps.

> Note: When creating your Object Storage service, select the ``Free`` storage type in order to avoid having to pay an upgrade fee.

## 2. Create IBM Cloud services

Create the following IBM Cloud service and name it wdc-NLU-service:

  * [**Watson Natural Language Understanding**](https://console.bluemix.net/catalog/services/natural-language-understanding)

  ![](doc/source/images/bluemix_service_nlu.png)

## 3. Create the notebook

* In [Watson Studio](https://dataplatform.ibm.com), click on `Create notebook` to create a notebook.
* Create a project if necessary, provisioning an object storage service if required.
* In the `Assets` tab, select the `Create notebook` option.
* Select the `From URL` tab.
* Enter a name for the notebook.
* Optionally, enter a description for the notebook.
* Enter this Notebook URL: https://github.com/IBM/watson-document-classifier/blob/master/notebooks/watson_document_classifier.ipynb
* Select the free Anaconda runtime.
* Click the `Create` button.

![](doc/source/images/create_notebook_from_url.png)

## 4. Add the data and configuration file

#### Add the data and configuration to the notebook

* From the `My Projects > Default` page, Use `Find and Add Data` (look for the `10/01` icon)
and its `Files` tab.
* Click `browse` and navigate to this repo `watson-document-classifier/data/sample_text.txt`
* Click `browse` and navigate to this repo `watson-document-classifier/configuration/sample_config.txt`

![](doc/source/images/add_file.png)

> Note:  It is possible to use your own data and configuration files.
If you use a configuration file from your computer, make sure to conform to the JSON structure given in `configuration/sample_config.txt`.

#### Fix-up file names for your own data and configuration files

If you use your own data and configuration files, you will need to update the variables that refer to the data and configuration files in the Jupyter Notebook.

In the notebook, update the global variables in the cell following `2.3 Global Variables` section.

Replace the `sampleTextFileName` with the name of your data file and `sampleConfigFileName` with your configuration file name.

![](doc/source/images/update_variables.png)

## 5. Update the notebook with service credentials

#### Add the Watson Natural Language Understanding credentials to the notebook
Select the cell below `2.1 Add your service credentials from IBM Cloud for the Watson services` section in the notebook to update the credentials for Watson Natural Langauage Understanding. 

Open the Watson Natural Language Understanding service in your [IBM Cloud Dashboard](https://console.bluemix.net/dashboard/services) and click on your service, which you should have named `wdc-NLU-service`.

Once the service is open click the `Service Credentials` menu on the left.

![](doc/source/images/service_credentials.png)

In the `Service Credentials` that opens up in the UI, select whichever `Credentials` you would like to use in the notebook from the `KEY NAME` column. Click `View credentials` and copy `username` and `password` key values that appear on the UI in JSON format.

![](doc/source/images/copy_credentials.png)

Update the `username` and `password` key values in the cell below `2.1 Add your service credentials from IBM Cloud for the Watson services` section.

![](doc/source/images/watson_nlu_credentials.png)

#### Add the Object Storage credentials to the notebook
* Select the cell below `2.2 Add your service credentials for Object Storage` section in the notebook to update the credentials for Object Store.
* Delete the contents of the cell
* Use `Find and Add Data` (look for the `10/01` icon) and its `Files` tab. You should see the file names uploaded earlier. Make sure your active cell is the empty one below `2.2 Add...`
* Select `Insert to code` (below your sample_text.txt).
* Click `Insert Crendentials` from drop down menu.
* Make sure the credentials are saved as `credentials_1`.

![](doc/source/images/objectstorage_credentials.png)

## 6. Run the notebook

When a notebook is executed, what is actually happening is that each code cell in
the notebook is executed, in order, from top to bottom.

> IMPORTANT: The first time you run your notebook, you will need to install the necessary
packages in section 1.1 and then `Restart the kernel`.

Each code cell is selectable and is preceded by a tag in the left margin. The tag
format is `In [x]:`. Depending on the state of the notebook, the `x` can be:

* A blank, this indicates that the cell has never been executed.
* A number, this number represents the relative order this code step was executed.
* A `*`, this indicates that the cell is currently executing.

There are several ways to execute the code cells in your notebook:

* One cell at a time.
  * Select the cell, and then press the `Play` button in the toolbar.
* Batch mode, in sequential order.
  * From the `Cell` menu bar, there are several options available. For example, you
    can `Run All` cells in your notebook, or you can `Run All Below`, that will
    start executing from the first cell under the currently selected cell, and then
    continue executing all cells that follow.
* At a scheduled time.
  * Press the `Schedule` button located in the top right section of your notebook
    panel. Here you can schedule your notebook to be executed once at some future
    time, or repeatedly at your specified interval.

## 7. Download the results

* To see the results, go to [Object Storage](https://console.bluemix.net/dashboard/storage)
* Click on the name of your object storage
* Click on the Container with the name you gave your Notebook
* Select `sample_text_classification.txt` file using select box to the left of the file listing
* Click the `SelectAction` button and use the `Download File` drop down menu to download `sample_text_classification.txt` file.

![](doc/source/images/objectstore_download_file.png)


## 8. Analyze the results

After running each cell of the notebook under `Classify text`, the results will display.

The configuration json controls the way the text is classified. The classification process is divided into stages - Base Tagging and Domain Tagging. The Base Tagging stage can be used to specify keywords based classification, regular expression based classification, and tagging based on chunking expressions. The Domain Tagging stage can be used to specify classification that is specific to the domain, in order to augment the results from Watson Natural Language Understanding.

![](doc/source/images/text_classify_config.png)

We can modify the configuration json to add more keywords or add regular expressions. In this way, we can augment the text classification without any changes to the code.
We can add more stages to the configuration json if required and enhance the text classification results with code modifications.

It can be seen from the classification results that the keywords and regular expressions specified in the configuration have been correctly classified
in the analyzed text that is displayed.

# Other scenarios and usecases 

[See USECASES.md.](USECASES.md)

> Note: The code and configuration provided in this repository can be modified to build a solution for the scenarios and usecases mentioned.


# Troubleshooting

[See DEBUGGING.md.](DEBUGGING.md)

# License

[Apache 2.0](LICENSE)
