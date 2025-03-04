---
title: "Quickstart: QnA Maker client library for Python"
description: This quickstart shows how to get started with the QnA Maker client library for Python.
ms.topic: include
ms.date: 06/18/2020
---

# [QnA Maker GA (stable release)](#tab/version-1)

Use the QnA Maker client library for python to:

* Create a knowledgebase
* Update a knowledgebase
* Publish a knowledgebase
* Get prediction runtime endpoint key
* Wait for long-running task
* Download a knowledgebase
* Get an answer from a knowledgebase
* Delete knowledge base

[Reference documentation](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker) | [Library source code](https://github.com/Azure/azure-sdk-for-python/tree/master/sdk/cognitiveservices/azure-cognitiveservices-knowledge-qnamaker) | [Package (PyPi)](https://pypi.org/project/azure-cognitiveservices-knowledge-qnamaker/0.2.0/) | [Python samples](https://github.com/Azure-Samples/cognitive-services-quickstart-code/blob/master/python/QnAMaker/sdk/quickstart.py)

# [Custom question answering (preview release)](#tab/version-2)

Use the QnA Maker client library for python to:

* Create a knowledgebase
* Update a knowledgebase
* Publish a knowledgebase
* Wait for long-running task
* Download a knowledgebase
* Get an answer from a knowledgebase
* Delete knowledge base

[Reference documentation](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker) | [Library source code](https://github.com/Azure/azure-sdk-for-python/tree/master/sdk/cognitiveservices/azure-cognitiveservices-knowledge-qnamaker) | [Package (PyPi)](https://pypi.org/project/azure-cognitiveservices-knowledge-qnamaker/) | [Python samples](https://github.com/Azure-Samples/cognitive-services-quickstart-code/blob/master/python/QnAMaker/sdk/preview-sdk/quickstart.py)

---

[!INCLUDE [Custom subdomains notice](../../../../includes/cognitive-services-custom-subdomains-note.md)]

## Prerequisites

# [QnA Maker GA (stable release)](#tab/version-1)

* Azure subscription - [Create one for free](https://azure.microsoft.com/free/cognitive-services)
* [Python 3.x](https://www.python.org/)
* Once you have your Azure subscription, create a [QnA Maker resource](https://ms.portal.azure.com/#create/Microsoft.CognitiveServicesQnAMaker) in the Azure portal to get your authoring key and endpoint. After it deploys, select **Go to resource**.
    * You will need the key and endpoint from the resource you create to connect your application to the QnA Maker API. You'll paste your key and endpoint into the code below later in the quickstart.
    * You can use the free pricing tier (`F0`) to try the service, and upgrade later to a paid tier for production.

# [Custom question answering (preview release)](#tab/version-2)

* Azure subscription - [Create one for free](https://azure.microsoft.com/free/cognitive-services)
* [Python 3.x](https://www.python.org/)
* * Custom question and answering requires a [Text Analytics resource](https://ms.portal.azure.com/?quickstart=true#create/Microsoft.CognitiveServicesTextAnalytics) with the custom question answering feature enabled to generate an API key and endpoint.
	* After your Text Analytics resource deploys, select **Go to resource**. You will need the key and endpoint from the resource you create to connect your application to the QnA Maker API. You'll paste your key and endpoint into the code below later in the quickstart.

---

## Setting up

### Install the client library

# [QnA Maker GA (stable release)](#tab/version-1)

After installing Python, you can install the client library with:

```console
pip install azure-cognitiveservices-knowledge-qnamaker==0.2.0
```

# [Custom question answering (preview release)](#tab/version-2)

After installing Python, you can install the client library with:

```console
pip install azure-cognitiveservices-knowledge-qnamaker
```

---

### Create a new python application

Create a new Python file named `quickstart-file.py` and import the following libraries.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Dependencies](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=Dependencies)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Dependencies](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=Dependencies)]

---

Create variables for your resource's Azure endpoint and key.

# [QnA Maker GA (stable release)](#tab/version-1)

- We use subscription key and authoring key interchangably. For more details on authoring key, follow [Keys in QnA Maker](../concepts/azure-resources.md?tabs=v1#keys-in-qna-maker).

- The value of QNA_MAKER_ENDPOINT has the format `https://YOUR-RESOURCE-NAME.cognitiveservices.azure.com`. Go to the Azure portal and find the QnA Maker resource you created in the prerequisites. Click on **Keys and Endpoint** page, under **resource management** to locate Authoring (Subscription) key and QnA Maker Endpoint.

 ![QnA Maker Authoring Endpoint](../media/keys-endpoint.png)

- The value of QNA_MAKER_RUNTIME_ENDPOINT has the format `https://YOUR-RESOURCE-NAME.azurewebsites.net`. Go to the Azure portal and find the QnA Maker resource you created in the prerequisites. Click on **Export Template** page, under **Automation** to locate the Runtime Endpoint.

 ![QnA Maker Runtime Endpoint](../media/runtime-endpoint.png)
   
- For production, consider using a secure way of storing and accessing your credentials. For example, [Azure key vault](../../../key-vault/general/overview.md) provides secure key storage.

[!code-python[Resource variables](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=Resourcevariables)]

# [Custom question answering (preview release)](#tab/version-2)

- We use subscription key and authoring key interchangably. For more details on authoring key, follow [Keys](../concepts/azure-resources.md?tabs=v2#keys-in-qna-maker).

- The value of QNA_MAKER_ENDPOINT has the format `https://YOUR-RESOURCE-NAME.cognitiveservices.azure.com`. Go to the Azure portal and find the Text Analytics resource you created in the prerequisites. Click on **Keys and Endpoint** page, under **resource management** to locate Authoring (Subscription) key and Endpoint.

> [!div class="mx-imgBorder"]
> ![Custom QnA Authoring Endpoint](../media/qnamaker-how-to-key-management/custom-qna-keys-and-endpoint.png)
 
- For production, consider using a secure way of storing and accessing your credentials. For example, [Azure key vault](../../../key-vault/general/overview.md) provides secure key storage.

[!code-python[Resource variables](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=Resourcevariables)]

---

## Object models

# [QnA Maker GA (stable release)](#tab/version-1)

[QnA Maker](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker) uses two different object models:
* **[QnAMakerClient](#qnamakerclient-object-model)** is the object to create, manage, publish, and download the knowledgebase.
* **[QnAMakerRuntime](#qnamakerruntimeclient-object-model)** is the object to query the knowledge base with the GenerateAnswer API and send new suggested questions using the Train API (as part of [active learning](../how-to/use-active-learning.md)).

# [Custom question answering (preview release)](#tab/version-2)

[QnA Maker](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker) uses the following object model:
* **[QnAMakerClient](#qnamakerclient-object-model)** is the object to create, manage, publish, download, and query the knowledgebase.

---

[!INCLUDE [Get KBinformation](./quickstart-sdk-cognitive-model.md)]

### QnAMakerClient object model

The authoring QnA Maker client is a [QnAMakerClient](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.qn_amaker_client.qnamakerclient) object that authenticates to Azure using Microsoft.Rest.ServiceClientCredentials, which contains your key.

Once the client is created, use the [Knowledge base](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebase_operations.knowledgebaseoperations) property to create, manage, and publish your knowledge base.

Manage your knowledge base by sending a JSON object. For immediate operations, a method usually returns a JSON object indicating status. For long-running operations, the response is the operation ID. Call the [operations.get_details](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebase_operations.knowledgebaseoperations#get-details-kb-id--custom-headers-none--raw-false----operation-config-) method with the operation ID to determine the [status of the request](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.operationstatetype).

### QnAMakerRuntimeClient object model

# [QnA Maker GA (stable release)](#tab/version-1)

The prediction QnA Maker client is a `QnAMakerRuntimeClient` object that authenticates to Azure using Microsoft.Rest.ServiceClientCredentials, which contains your prediction runtime key, returned from the authoring client call, [client.EndpointKeysOperations.get_keys](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.endpoint_keys_operations.endpointkeysoperations#get-keys-custom-headers-none--raw-false----operation-config-) after the knowledgebase is published.

Use the `generate_answer` method to get an answer from the query runtime.

# [Custom question answering (preview release)](#tab/version-2)

Custom question answering does not require the use of the QnAMakerRuntimeClient object. Instead, you call [generate_answer](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebase_operations.knowledgebaseoperations#generate-answer-kb-id--generate-answer-payload--custom-headers-none--raw-false----operation-config-) directly on the [QnAMakerClient](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.qn_amaker_client.qnamakerclient) object.

---

## Authenticate the client for authoring the knowledge base

Instantiate a client with your endpoint and key. Create an CognitiveServicesCredentials object with your key, and use it with your endpoint to create an [QnAMakerClient](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.qn_amaker_client.qnamakerclient) object.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Authorization to resource key](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=AuthorizationAuthor)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Authorization to resource key](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=AuthorizationAuthor)]

---

## Create a knowledge base

Use the client object to get a [knowledge base operations](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebaseoperations) object.

A knowledge base stores question and answer pairs for the [CreateKbDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.createkbdto) object from three sources:

* For **editorial content**, use the [QnADTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.qnadto) object.
    * To use metadata and follow-up prompts, use the editorial context, because this data is added at the individual QnA pair level.
* For **files**, use the [FileDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.filedto) object. The FileDTO includes the filename as well as the public URL to reach the file.
* For **URLs**, use a list of strings to represent publicly available URLs.

Call the [create](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebaseoperations#create-create-kb-payload--custom-headers-none--raw-false----operation-config-) method then pass the returned operation ID to the [Operations.getDetails](#get-status-of-an-operation) method to poll for status.

The final line of the following code returns the knowledge base ID from the response from MonitorOperation.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Create knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=CreateKBMethod)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Create knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=CreateKBMethod)]

---

Make sure the include the [`_monitor_operation`](#get-status-of-an-operation) function, referenced in the above code, in order to successfully create a knowledge base.

## Update a knowledge base

You can update a knowledge base by passing in the knowledge base ID and an [UpdateKbOperationDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.updatekboperationdto) containing [add](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.updatekboperationdtoadd), [update](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.updatekboperationdtoupdate), and [delete](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.updatekboperationdtodelete) DTO objects to the [update](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebase_operations.knowledgebaseoperations) method. Use the [Operation.getDetail](#get-status-of-an-operation) method to determine if the update succeeded.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Update a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=UpdateKBMethod)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Update a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=UpdateKBMethod)]

---

Make sure the include the [`_monitor_operation`](#get-status-of-an-operation) function, referenced in the above code, in order to successfully update a knowledge base.

## Download a knowledge base

Use the [download](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebaseoperations) method to download the database as a list of [QnADocumentsDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.qnadocumentsdto). This is _not_ equivalent to the QnA Maker portal's export from the **Settings** page because the result of this method is not a TSV file.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Download a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=DownloadKB)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Download a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=DownloadKB)]

---

## Publish a knowledge base

Publish the knowledge base using the [publish](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebaseoperations#publish-kb-id--custom-headers-none--raw-false----operation-config-) method. This takes the current saved and trained model, referenced by the knowledge base ID, and publishes that at an endpoint.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Publish a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=PublishKB)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Publish a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=PublishKB)]

---

## Query a knowledge base

# [QnA Maker GA (stable release)](#tab/version-1)

### Get query runtime key

Once a knowledgebase is published, you need the query runtime key to query the runtime. This isn't the same key used to create the original client object.

Use the [EndpointKeysOperations.get_keys](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.endpointkeysoperations#get-keys-custom-headers-none--raw-false----operation-config-) method to get the [EndpointKeysDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.endpointkeysdto) class.

Use either of the key properties returned in the object to query the knowledgebase.

[!code-python[Get query runtime key](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=GetQueryEndpointKey)]

### Authenticate the runtime for generating an answer

Create a [QnAMakerRuntimeClient](/javascript/api/@azure/cognitiveservices-qnamaker-runtime/qnamakerruntimeclient) to query the knowledge base to generate an answer or train from active learning.

[!code-python[Authenticate the runtime](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=AuthorizationQuery)]

Use the QnAMakerRuntimeClient to get an answer from the knowledge or to send new suggested questions to the knowledge base for [active learning](../index.yml).

### Generate an answer from the knowledge base

Generate an answer from a published knowledge base using the QnAMakerRuntimeClient.runtime.generate_answer method. This method accepts the knowledge base ID and the [QueryDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.querydto). Access additional properties of the QueryDTO, such a Top and Context to use in your chat bot.

[!code-python[Generate an answer from a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=GenerateAnswer)]

# [Custom question answering (preview release)](#tab/version-2)

### Generate an answer from the knowledge base

Generate an answer from a published knowledge base using the [generate_answer](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebaseoperations#generate-answer-kb-id--generate-answer-payload--custom-headers-none--raw-false----operation-config-) method. This method accepts the knowledge base ID and the [QueryDTO](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.querydto). Access additional properties of the QueryDTO, such a Top and Context to use in your chat bot.

[!code-python[Generate an answer from a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=GenerateAnswer)]

---

This is a simple example of querying the knowledge base. To understand advanced querying scenarios, review [other query examples](../quickstarts/get-answer-from-knowledge-base-using-url-tool.md?pivots=url-test-tool-curl#use-curl-to-query-for-a-chit-chat-answer).

## Delete a knowledge base

Delete the knowledge base using the [delete](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.operations.knowledgebaseoperations#delete-kb-id--custom-headers-none--raw-false----operation-config-) method with a parameter of the knowledge base ID.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Delete a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=DeleteKB)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Delete a knowledge base](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=DeleteKB)]

---

## Get status of an operation

Some methods, such as create and update, can take enough time that instead of waiting for the process to finish, an [operation](/python/api/azure-cognitiveservices-knowledge-qnamaker/azure.cognitiveservices.knowledge.qnamaker.models.operation(class)) is returned. Use the operation ID from the operation to poll (with retry logic) to determine the status of the original method.

The _setTimeout_ call in the following code block is used to simulate asynchronous code. Replace this with retry logic.

# [QnA Maker GA (stable release)](#tab/version-1)

[!code-python[Monitor an operation](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/quickstart.py?name=MonitorOperation)]

# [Custom question answering (preview release)](#tab/version-2)

[!code-python[Monitor an operation](~/cognitive-services-quickstart-code/python/QnAMaker/sdk/preview-sdk/quickstart.py?name=MonitorOperation)]

---

## Run the application

Run the application with the python command on your quickstart file.

```console
python quickstart-file.py
```

# [QnA Maker GA (stable release)](#tab/version-1)

The source code for this sample can be found on [GitHub](https://github.com/Azure-Samples/cognitive-services-quickstart-code/blob/master/python/QnAMaker/sdk/quickstart.py).

# [Custom question answering (preview release)](#tab/version-2)

The source code for this sample can be found on [GitHub](https://github.com/Azure-Samples/cognitive-services-quickstart-code/blob/master/python/QnAMaker/sdk/preview-sdk/quickstart.py).

---