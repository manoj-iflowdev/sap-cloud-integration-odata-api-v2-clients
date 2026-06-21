<h1 align="center">Welcome to SAP Cloud Integration OData API Clients</h1>

## TL;DR

To consume the SAP Cloud Integration APIs, you must install the SAP Cloud SDK and utilize the generated clients. It is necessary to properly configure tsconfig when using Typescript, which can be challenging as it may not always be compatible with your project.

Additionally, these files begin to appear in every project, leading to unnecessary boilerplate in many repositories within SAP projects.

Now you can simply run `npm install ts-sap-cloud-odata-api-v2-client` and start using the generated clients immediately without any stress.

Read more: https://sap.github.io/cloud-sdk/docs/js/getting-started

Process followed: https://sap.github.io/cloud-sdk/docs/js/features/odata/generate-client

## !! Disclaimer !!

Do not use the npm-package in a production environment as it is still in beta. The APIs and features covered have not changed in about two years, making them very stable.

The intention here is not to centralize all SAP CPI clients and maintain them into a micro-node module.

Regarding the npm package, you do not need to use it if it does not suit your needs. You can use the files in this repository as examples and copy the entire repository to your versioning system if you wish to make changes and tweaks. Any pull requests attempting to modify the generated code will not be accepted.

It's just a code that can be used as quick start, example and to be copied.

This project is actively maintained. We encourage you to use it, contribute, and provide feedback. You are welcome to clone the repository, open the project in your preferred IDE, and explore the sap-cloud-sdk-generator models.

## Why

This code was created with the help of the SAP Cloud SDK, there's no custom code or layers added to it. It's exactly the same output of
using sap-cloud-sdk and generating clients from the odata package.

The benefits of this package depend on the use case. It is currently being utilized to, so please refer to the Disclaimer section above.
1. Automate the ingestion of logs from OData into DataLog automatically.
2. Write xslts in external IDEs like VSCode using unit tests for mappings, then using the api in CD pipeline to push these artifacts to
   low environment IFlows well tested and covered.
4. Make it possible to create Pipeline for CI/CD that runs e2e automated and assert odata logs and also keep the IFlows external parameters
   committed using GitOps approach.
5. Internally, it's easy to apply security scans and fixes in a centralized generated code than a distributed approach across all teams. If you don't scan generated code for issues you may ignore this item.

## Features

Clients were generated for the following APIs in [Cloud Integration](https://api.sap.com/package/CloudIntegrationAPI/odata):


| Name | Version | Generated |
| ---- | ---- | --------- |
| [IntegrationContent](https://api.sap.com/api/IntegrationContent/resource/Integration_Package_Discover) | 1.0.0 | Yes |
| [LogFiles](https://api.sap.com/api/LogFiles/resource/Log_Files) | 1.0.0 | Yes |
| [MessageProcessingLogs](https://api.sap.com/api/MessageProcessingLogs/resource/Logs) | 1.0.0 | Yes |
| [MessageStore](https://api.sap.com/api/MessageStore/resource/Entries) | 1.0.0 | Yes |
| [PartnerDirectory](https://api.sap.com/api/PartnerDirectory/resource/Alternative_Partners) | 1.0.0 | Yes |
| [SecurityContent](https://api.sap.com/api/SecurityContent/resource/Certificate) | 1.0.0 | Yes |


## Install

```sh
npm i ts-sap-cloud-odata-api-v2-client
```

## Dependencies
```sh
npm i @sap-cloud-sdk/connectivity #required
npm i @sap-cloud-sdk/odata-v2 #optional
```

## Usage

Now you can simply use the generated clients in your code. The entire interface was kept from the SDK, and you can refer to the [documentation](https://sap.github.io/cloud-sdk/docs/js/getting-started) to learn more.

[How to execute a request](https://sap.github.io/cloud-sdk/docs/js/features/odata/execute-request)


Each client is isolated in a module that can be imported using `'ts-sap-cloud-odata-api-v2-client/{APINAME}'`.
This is necessary to avoid conflicts with other modules as they are all generated separately.

*Example**

```js
import { registerDestination } from '@sap-cloud-sdk/connectivity'
import { messageProcessingLogs, MessageProcessingLogsType } from "ts-sap-cloud-odata-api-v2-client/MessageProcessingLogsClient";

async function example(name: string, url: string) {

    await registerDestination(
        {
            name: name, // choose name
            url: url // add url to your tenant
        },
    );

    const basePath = "/api/v1" // change if needed
    
    const requestBuilder = messageProcessingLogs<MessageProcessingLogsType>().messageProcessingLogsApi.requestBuilder().getAll()

    const getAll = requestBuilder.setBasePath(basePath).addCustomHeaders({ 'authorization': `Bearer ...` })

    return getAll.execute({ destinationName: name })
}
```

## Known issues

This library is still in beta. Please report any bugs or feature requests to the GitHub issue tracker.

Please use the version `1.4.x` or above. This library is compiled to es6 with commonjs to increase compatibility.


## Show your support

Give a star if this project helped you!

If you would like to ask about features, other API clients, report bugs, or seek help, please feel free to create an issue in the GitHub repository.
[Github Issues](https://github.com/GiuseppeMP/sap-cloud-integration-odata-api-v2-clients/issues/new)

***
_This README was generated with love by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_

## About the Maintainer

This project is currently maintained by Manoj Gali.

Manoj is a Senior SAP CPI Consultant with over 5 years of experience in SAP integration technologies, specializing in SAP CPI, PI/PO, and hybrid integration landscapes. He is dedicated to designing, developing, and optimizing scalable integration solutions, ensuring secure, high-performance data exchange across SAP and non-SAP systems. His expertise includes Groovy Scripting, XSLT, and User-Defined Functions (UDFs).

Feel free to connect or reach out:
- Email: manoj.gali695@gmail.com
- GitHub: Manoj Gali
- LinkedIn: Manoj Gali