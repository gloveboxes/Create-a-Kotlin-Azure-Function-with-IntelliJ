# Get started with the new Kotlin Azure Functions Archetype and IntelliJ IDEA

|Author|[Dave Glover](https://developer.microsoft.com/advocates/dave-glover?WT.mc_id=iot-0000-dglover), Microsoft Cloud Developer Advocate |
|----|---|
|GitHub| [Get started with the new Kotlin Azure Functions Archetype and IntelliJ](https://github.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ)|
|Platform| [Azure Functions](https://docs.microsoft.com/azure/azure-functions?WT.mc_id=iot-0000-dglover)|
|Programming Language| Kotlin|
|Date|As at June 2019|

This is an end to end walkthrough for creating Kotlin Azure Functions.

Kotlin is an emerging development language rated as one of the most loved languages in the last [Stack Overflow Developer Survey](https://insights.stackoverflow.com/survey/2018#technology). It is becoming the default language for Android Development and being eyed with interested by those with investments in Java and looking for a more modern JVM language.

## 1. <a name='ReferenceDocumentation'></a>Reference Documentation

- [Create your first Azure function with Java and IntelliJ](https://docs.microsoft.com/azure/azure-functions/functions-create-maven-intellij?WT.mc_id=iot-0000-dglover)
- [Azure Functions Java developer guide](https://docs.microsoft.com/azure/azure-functions/functions-reference-java?WT.mc_id=iot-0000-dglover)
- [Library for Azure Java Functions](https://github.com/Azure/azure-functions-java-library)
- [Azure Maven Archetypes](https://github.com/microsoft/azure-maven-archetypes)
- [Register Azure Functions binding extensions](https://docs.microsoft.com/tn-ba/azure/azure-functions/functions-bindings-register?WT.mc_id=iot-0000-dglover)
- [Maven Plugin for Azure Functions](https://docs.microsoft.com/java/api/overview/azure/maven/azure-functions-maven-plugin/readme?view=azure-java-stable&WT.mc_id=iot-0000-dglover)
- [Azure Toolkit for IntelliJ](https://docs.microsoft.com/java/azure/intellij/azure-toolkit-for-intellij?view=azure-java-stable&WT.mc_id=iot-0000-dglover)

##  2. <a name='Setupyourdevelopmentenvironment'></a>Set up your development environment

To develop a function with Java and IntelliJ, install the following software:

- [Java Developer Kit](https://www.azul.com/downloads/zulu/) (JDK), version 8
- [Apache Maven](https://maven.apache.org), version 3.0 or higher
- [IntelliJ IDEA](https://www.jetbrains.com/idea/download), Community or Ultimate versions
- [Azure Toolkit for IntelliJ](https://docs.microsoft.com/java/azure/intellij/azure-toolkit-for-intellij-installation?view=azure-java-stable&WT.mc_id=iot-0000-dglover) (Optional)
- [Azure CLI](https://docs.microsoft.com/cli/azure?WT.mc_id=iot-0000-dglover)
- [Azure Functions Core Tools, version 2](https://docs.microsoft.com/azure/azure-functions/functions-run-local?WT.mc_id=iot-0000-dglover)

> The JAVA_HOME environment variable must be set to the install location of the JDK to complete the steps in this article.

## 3. <a name='CreateanAzureFunctionproject'></a>Create a Kotlin Azure Function Project

1. From IntelliJ IDEA, select **Create New Project**.  
1. In the **New Project** window, select **Maven** from the left pane.
1. Select the **Create from archetype** check box, and then select **Add Archetype** for the [azure-functions-kotlin-archetype](https://mvnrepository.com/artifact/com.microsoft.azure/azure-functions-kotlin-archetype).
1. In the **Add Archetype** window, complete the fields as follows:
    - _GroupId_: com.microsoft.azure
    - _ArtifactId_: azure-functions-kotlin-archetype
    - _Version_: Use the latest version from [the central repository](https://mvnrepository.com/artifact/com.microsoft.azure/azure-functions-kotlin-archetype)

    Select **OK**, and then select **Next**.
    ![create new Kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/masterhttps://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/create-new-project.png)
1. Enter your details for the current project, and select **Next**.
![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/masterhttps://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/create-new-project-properties.png)
Define the GroupId and the ArtifactId for the project This information is added to the project pom.xml. The ArtifactId forms part of the Azure Function name in the pom.xml file. For more information see [Creating a new Maven project](https://www.jetbrains.com/help/idea/2018.3/maven-support.html?utm_content=2018.3&utm_medium=link&utm_source=product&utm_campaign=IC#create_new_maven_project)
1. Confirm the Maven Project Settings, and select **Next**.
![Maven summary](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/create-new-project-summary.png)
1. Confirm Project Name and Location, and select **Finish**.
![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/create-new-project-confirmation.png)
The project structure will be created.

Maven creates the project files in a new folder with the same name as the project _ArtifactId_ value. The project's generated code is a simple [HTTP-triggered](https://docs.microsoft.com/azure/azure-functions/functions-bindings-http-webhook?WT.mc_id=iot-0000-dglover) function that echoes the body of the triggering HTTP request.

## 4. <a name='EnableAuto-Import'></a>Enable Auto-Import

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/create-new-project-enable-auto-import.png)

## 5. <a name='AzureConfiguration'></a>Azure Configuration

By default, the pom.xml file is opened when the project is created.

You can change the following project properties in the pom.xml file

1. Azure Function App Name
2. Azure Function App Region

Run the following command for a complete list of regions. Choose the location by the "name" field in the returned JSON array.

```bash
az account list-locations
```

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/create-new-project-skelton.png)

## 6. <a name='OpenthedefaultHttpTrigger'></a>Open the default Http Trigger

The Azure Functions Maven Archetype will create an example Http Trigger. You will find this by navigating the **src** project directory.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-default-http-trigger.png)

## 7. <a name='CleanandPackagetheProject'></a>Clean and Package the Project

From the Maven pop-out tab, expand **Lifecycle**, then run the **clean** followed by the **package** commands. This will build the Kotlin project.

![](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-clean-package.png)

## 8. <a name='ExecuteAzureFunctionsRun'></a>Execute Azure Functions Run

From the Maven pop-out tab, expand **Plugins**, then expand **azure-functions**, then select **azure-functions:run**. This will start the Azure Functions Core Tools and bootstrap your Kotlin Azure Function.

To test the function click the http://localhost:7071/api/HttpTrigger-Kotlin link

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-azure-functions-run.png)

**TIP**: The function runs in the context of a local process called **func** on port 7071. Sometimes this process does not close properly. If this happens, then next time you run the function it will complain that port 7071 is already open. You need to close the **func** process manually from the task/process manager of your operating system.

## 9. <a name='PassinaparameterontheQueryString'></a>Pass in a parameter on the Query String

In the browser add a name parameter to the query string. For example, http://localhost:7071/api/HttpTrigger-Kotlin?name=dave and you will see the webpage echos the value passed in for name.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-test-http-trigger.png)

Alternatively, you can trigger the function from the command line using curl in a new terminal window:

```bash
curl -w '\n' -d Dave http://localhost:7071/api/HttpTrigger-Kotlin
```

## 10. <a name='Stopthefunction'></a>Stop the function

Click the stop icon to stop the function from running.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-azure-functions-stop.png)

## 11. <a name='EnableDebugging'></a>Enable Debugging

Right mouse click on the **azure-functions:run** Maven Archetype and select **Create 'glovebox-function [...**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-enable-debug-azure-function-maven-debug.png)

## 12. <a name='CreateRunDebugConfiguration'></a>Create Run/Debug Configuration

1. Rename the configuration to highlight that **package** will be run before azure-functions:run.
2. Add **-DenableDebug** to the command line.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-enable-debug-azure-function-maven-debug-configure.png)

Add **package**

![](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-run-edit-configurations-add-package.png)

Click **OK**.

![](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-run-edit-configurations-completed.png)

Click **OK**

## 13. <a name='EnableJavaDebuggerAttach'></a>Enable JVM Debugger Attach

From **Run** menu, select **Edit Configuration**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-run-edit-configurations.png)

## 14. <a name='AddNewConfiguration'></a>Add New Configuration

Click the **+** sign, then select **Remote**.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-run-edit-configurations-add-remote-config.png)

## 15. <a name='NametheNewConfiguration'></a>Name the New Configuration

In this case. the configuration is named **Attach Debugger**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-run-edit-configurations-add-remote-attach-debugger.png)

Click **OK**

## 16. <a name='SetabreakpointintheKotlinAzureFunctionsource'></a>Set a breakpoint in the Kotlin Azure Function source

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-debug-set-breakpoint.png)

## 17. <a name='RunDebuggerEnabledConfiguration'></a>Run Debugger Enabled Configuration

From the **run/debug configuration selector** select the Maven azure-functions:run configuration. and the click the green start icon or press Shift+F10.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-debug-run-debug-enabled-maven.png)

## 18. <a name='AttachtheDebugger'></a>Attach the Debugger

From the **run/debug configuration selector** select the **Attach Debugger** configuration and click the green start debugger icon or press Shift+F9.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-debug-debugger-attached.png)

## 19. <a name='InitiatetheHttpTriggerinDebugMode'></a>Initiate the Http Trigger in Debug Mode

1. Select the **Run** tab.

2. Click the http://localhost:7071/api/HttpTrigger-Kotlin link to initiate the Http Trigger.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-debug-switch-to-run.png)

## 20. <a name='StepthroughtheHttpTriggerAzureFunctionwiththeDebugger'></a>Step through the Http Trigger Azure Function with the Debugger

Using the debugger controls, step through the Azure Function code.

![kotlin debugging](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-debug-step-through-code.png)

## 21. <a name='StoptheDebuggerandAzureFunction'></a>Stop the Debugger and Azure Function

Click the Stop icon to detach the debugger and stop the Azure Function

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/project-debugger-stop.png)

## 22. <a name='AddingnewAzureFunctionTriggers'></a>Adding new Azure Function Triggers

[azure-functions:add](https://docs.microsoft.com/java/api/overview/azure/maven/azure-functions-maven-plugin/readme?view=azure-java-stable&WT.mc_id=iot-0000-dglover#azure-functionsadd&WT.mc_id=github-blog-dglover)

The azure-functions:add Maven archetype supports the following trigger types.

- HTTP Trigger
- Azure Storage Blob Trigger
- Azure Storage Queue Trigger
- Timer Trigger
- Event Grid Trigger
- Event Hub Trigger
- Cosmos DB Trigger
- Service Bus Queue Trigger
- Service Bus Topic Trigger

From the Maven pop-out, under Plugins, select **azure-functions:add**

![Azure functions add](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/azure-function-add.png)

## 23. <a name='DeployingKotlinAzureFunctionstoAzure'></a>Deploying Kotlin Azure Functions to Azure

[azure-functions:deploy](https://docs.microsoft.com/java/api/overview/azure/maven/azure-functions-maven-plugin/readme?view=azure-java-stable&WT.mc_id=iot-0000-dglover#azure-functionsdeploy&WT.mc_id=github-blog-dglover)

To deploy the staging directory to target Azure Functions. If target Azure Functions does not exist already, it will be created.

![Azure functions deploy](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/azure-function-deploy.png)

## Congratulations

You have created your first Kotlin based Azure Function

![Congratulations](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/congratulations.jpg)

## Next

Try out the [Building a Serverless IoT Solution with Kotlin Azure Functions and SignalR](https://dev.to/azure/building-a-serverless-iot-solution-with-kotlin-azure-functions-and-signalr-2lpg)

![Building a Serverless IoT Solution with Kotlin Azure Functions and SignalR](https://raw.githubusercontent.com/gloveboxes/Create-a-Kotlin-Azure-Function-with-IntelliJ/master/resources/iot-solution-architecture.png)
