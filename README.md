# Create a Kotlin Azure Function with IntelliJ

|Author|[Dave Glover](https://developer.microsoft.com/en-us/advocates/dave-glover), Microsoft Cloud Developer Advocate |
|----|---|
|Solution| [Creating your first Kotlin Azure Function](https://github.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ)|
|Documentation|[README](https://gloveboxes.github.io/Creating-an-image-recognition-solution-with-Azure-IoT-Edge-and-Azure-Cognitive-Services/) |
|Platform| [Azure Functions](https://docs.microsoft.com/en-us/azure/azure-functions?WT.mc_id=devto-blog-dglover)|
|Programming Language| Kotlin|
|Date|As at April 2019|

This is an end to end walk through for creating Kotlin Azure Functions.

Kotlin is an emerging development language rated as one of the most loved languages in the last [Stack Overflow Developer Survey](https://insights.stackoverflow.com/survey/2018#technology). It is becoming the default language for Android Development and being eyed with interested by those with investments in Java and looking for a more modern JVM language.

##  1. <a name='ReferenceDocumentation'></a>Reference Documentation

- [Create your first Azure function with Java and IntelliJ](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-maven-intellij?WT.mc_id=devto-blog-dglover)
- [Azure Functions Java developer guide](https://docs.microsoft.com/en-us/azure/azure-functions/functions-reference-java?WT.mc_id=devto-blog-dglover)
- [Library for Azure Java Functions](https://github.com/Azure/azure-functions-java-library)
- [Register Azure Functions binding extensions](https://docs.microsoft.com/bs-latn-ba/azure/azure-functions/functions-bindings-register?WT.mc_id=devto-blog-dglover)
- [Maven Plugin for Azure Functions](https://docs.microsoft.com/en-us/java/api/overview/azure/maven/azure-functions-maven-plugin/readme?view=azure-java-stable&WT.mc_id=devto-blog-dglover)
- [Azure Toolkit for IntelliJ](https://docs.microsoft.com/en-us/java/azure/intellij/azure-toolkit-for-intellij?view=azure-java-stable&WT.mc_id=devto-blog-dglover)

##  2. <a name='Setupyourdevelopmentenvironment'></a>Set up your development environment

To develop a function with Java and IntelliJ, install the following software:

- [Java Developer Kit](https://www.azul.com/downloads/zulu/) (JDK), version 8
- [Apache Maven](https://maven.apache.org), version 3.0 or higher
- [IntelliJ IDEA](https://www.jetbrains.com/idea/download), Community or Ultimate versions with Maven
- [Azure CLI](https://docs.microsoft.com/cli/azure?WT.mc_id=devto-blog-dglover)
- [Azure Functions Core Tools, version 2](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local?WT.mc_id=devto-blog-dglover)

> The JAVA_HOME environment variable must be set to the install location of the JDK to complete the steps in this article.

##  3. <a name='CreateanAzureFunctionproject'></a>Create an Azure Function project

1. In IntelliJ IDEA, select **Create New Project**.  
1. In the **New Project** window, select **Maven** from the left pane.
1. Select the **Create from archetype** check box, and then select **Add Archetype** for the [azure-functions-kotlin-archetype](https://mvnrepository.com/artifact/com.microsoft.azure/azure-functions-kotlin-archetype).
1. In the **Add Archetype** window, complete the fields as follows:
    - _GroupId_: com.microsoft.azure
    - _ArtifactId_: azure-functions-kotlin-archetype
    - _Version_: Use the latest version from [the central repository](https://mvnrepository.com/artifact/com.microsoft.azure/azure-functions-kotlin-archetype)
1. Select **OK**, and then select **Next**.
1. Enter your details for the current project, and select **Finish**.

Maven creates the project files in a new folder with the same name as the _ArtifactId_ value. The project's generated code is a simple [HTTP-triggered](/azure/azure-functions/functions-bindings-http-webhook) function that echoes the body of the triggering HTTP request.

![create new Kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/create-new-project.png)

##  4. <a name='SpecifytheMavenbasicElements'></a>Specify the Maven basic Elements

Define the GroupId and the ArtifactId for the project This information is added to the project pom.xml.

The ArtifactId forms part of the Azure Function name in the pom.xml file.

For more information see [Creating a new Maven project](https://www.jetbrains.com/help/idea/2018.3/maven-support.html?utm_content=2018.3&utm_medium=link&utm_source=product&utm_campaign=IC#create_new_maven_project)

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/create-new-project-properties.jpg)

##  5. <a name='ConfirmtheMavenProjectsettings'></a>Confirm the Maven Project settings

![Maven summary](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/create-new-project-summary.jpg)

##  6. <a name='ConfirmProjectNameandLocation'></a>Confirm Project Name and Location

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/create-new-project-confirmation.jpg)

The project structure will be created.

##  7. <a name='EnableAuto-Import'></a>Enable Auto-Import

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/create-new-project-enable-auto-import.jpg)

##  8. <a name='AzureConfiguration'></a>Azure Configuration

By default the pom.xml file is opened when the project is created.

You can set the following project properties in the pom.xml file

1. Azure Function App Name
2. Azure Function App Region

Run the following command for a complete list of regions. Choose the location by the "name" field in the returned JSON array.

```bash
az account list-locations
```

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/create-new-project-skelton.jpg)

##  9. <a name='OpenthedefaultHttpTrigger'></a>Open the default Http Trigger

The Azure Functions Maven Archetype will create an example Http Trigger. You will find this by navigating the **src** project directory.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-default-http-trigger.jpg)

##  10. <a name='ConverttheJavaAzureFunctiontoKotlinfile'></a>Convert the Java Azure Function to Kotlin file

Right mouse click the default Java Function named **Function** and select **Convert Java File to Kotlin File**. And voila, the Java file magically converts a Kotlin project.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-convert-to-kotlin.jpg)

The default Azure Function converted from Java will now look like beautiful Kotlin.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-converted-to-kotlin.jpg)

##  11. <a name='ConfiguretheProjectforKotlin'></a>Configure the Project for Kotlin

From the **Tools** menu, select **Kotlin**, then **Configure Kotlin in Project**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-configure-kotlin-in-project.jpg)

##  12. <a name='EnableAllModulescontainingKotlinfiles'></a>Enable All Modules containing Kotlin files

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-configure-kotlin-in-project-confirm.jpg)

##  13. <a name='CleanandPackagetheProject'></a>Clean and Package the Project

From the Maven pop-out tab, expand **Lifecycle**, then run the **clean** followed by the **package** commands. This will build the Kotlin project.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-clean-package-results.jpg)

##  14. <a name='ExecuteAzureFunctionsRun'></a>Execute Azure Functions Run

From the Maven pop-out tab, expand **Plugins**, then run the **azure-functions:run**. This will start the Azure Functions Core Tools and bootstrap your Kotlin Azure Function.

To test the function click the http://localhost:7071/api/HttpTrigger-Java link

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-azure-functions-run.jpg)

##  15. <a name='PassinaparameterontheQueryString'></a>Pass in a parameter on the Query String

In the browser add a name parameter to the query string. For example, http://localhost:7071/api/HttpTrigger-Java?name=dave and you will see the webpage echos the value passed in for name.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-test-http-trigger.jpg)

##  16. <a name='Stopthefunction'></a>Stop the function

Click the stop icon to stop the function from running.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-azure-functions-stop.jpg)

##  17. <a name='EnableDebugging'></a>Enable Debugging

Right mouse click on the **azure-functions:run** Maven Archetype and select **Create 'glovebox-function [...**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-enable-debug-azure-function-maven-debug.jpg)

##  18. <a name='CreateRunDebugConfiguration'></a>Create Run/Debug Configuration

Add **-DenableDebug** to the command line.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-enable-debug-azure-function-maven-debug-configure.jpg)

##  19. <a name='EnableJavaDebuggerAttach'></a>Enable Java Debugger Attach

From **Run** menu, select **Edit Configuration**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-run-edit-configurations.jpg)

##  20. <a name='AddNewConfiguration'></a>Add New Configuration

Click the **+** sign, then select **Remote**.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-run-edit-configurations-add-remote-config.jpg)

##  21. <a name='NametheNewConfiguration'></a>Name the New Configuration

In this case the configuration is named **Attach Debugger**

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-run-edit-configurations-add-remote-attach-debugger.jpg)

##  22. <a name='SetabreakpointintheKotlinAzureFunctionsource'></a>Set a breakpoint in the Kotlin Azure Function source

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-debug-set-breakpoint.jpg)

##  23. <a name='RunDebuggerEnabledConfiguration'></a>Run Debugger Enabled Configuration

From the **run/debug configuration selector** select the Maven azure-functions:run configuration. and the click the green start icon or press Shift+F10.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-debug-run-debug-enabled-maven.jpg)

##  24. <a name='AttachtheDebugger'></a>Attach the Debugger

From the **run/debug configuration selector** select the **Attach Debugger** configuration and click the green start debugger icon or press Shift+F9.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-debug-debugger-attached.jpg)

##  25. <a name='InitiatetheHttpTriggerinDebugMode'></a>Initiate the Http Trigger in Debug Mode

Click the http://localhost:7071/api/HttpTrigger-Java link to initiate the Http Trigger.

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-debug-switch-to-run.jpg)

##  26. <a name='StepthroughtheHttpTriggerAzureFunctionwiththeDebugger'></a>Step through the Http Trigger Azure Function with the Debugger

Using the debugger controls, step through the Azure Function code.

![kotlin debugging](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-debug-step-through-code.jpg)

##  27. <a name='StoptheDebuggerandAzureFunction'></a>Stop the Debugger and Azure Function

Click the Stop icon to detach the debugger and stop the Azure Function

![create new kotlin project](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/project-debugger-stop.jpg)

##  28. <a name='AddingnewAzureFunctionTriggers'></a>Adding new Azure Function Triggers

[azure-functions:add](https://docs.microsoft.com/en-us/java/api/overview/azure/maven/azure-functions-maven-plugin/readme?view=azure-java-stable#azure-functionsadd&WT.mc_id=devto-blog-dglover)

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

![Azure functions add](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/azure-function-add.jpg)

##  29. <a name='DeployingKotlinAzureFunctionstoAzure'></a>Deploying Kotlin Azure Functions to Azure

[azure-functions:deploy](https://docs.microsoft.com/en-us/java/api/overview/azure/maven/azure-functions-maven-plugin/readme?view=azure-java-stable#azure-functionsdeploy&WT.mc_id=devto-blog-dglover)

To deploy the staging directory to target Azure Functions. If target Azure Functions does not exist already, it will be created.

![Azure functions deploy](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/azure-function-deploy.jpg)

## 30. Building an End to End Secure, Scalable IoT Serverless Solution

The next article will be about creating an end to end IoT Serverless solution with Kotlin Azure Functions and Azure SignalR.

![end to end solution](https://raw.githubusercontent.com/gloveboxes/Create-your-first-Azure-function-with-Kotlin-and-IntelliJ/master/resources/kotlin-end-to-end-iot-serverless-functions-signalr.png)