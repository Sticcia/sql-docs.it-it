---
title: 'Procedura dettagliata: Estendere la distribuzione del progetto di database per analizzare il piano di distribuzione | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9ead8470-93ba-44e3-8848-b59322e37621
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: daae5aa71c227591a3349de4abd6526e83131f8c
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52512615"
---
# <a name="walkthrough-extend-database-project-deployment-to-analyze-the-deployment-plan"></a>Procedura dettagliata: estendere la distribuzione del progetto di database per analizzare il piano di distribuzione
È possibile creare collaboratori alla distribuzione per eseguire azioni personalizzate quando si distribuisce un progetto SQL. È possibile creare un elemento DeploymentPlanModifier o DeploymentPlanExecutor. Utilizzare DeploymentPlanModifier per modificare il piano prima di eseguirlo e DeploymentPlanExecutor per eseguire operazioni mentre il piano è in esecuzione. In questa procedura dettagliata viene creato un elemento DeploymentPlanExecutor denominato DeploymentUpdateReportContributor che crea un report sulle azioni eseguite quando si distribuisce un progetto di database. Poiché questo collaboratore alla compilazione accetta un parametro per controllare se il report viene generato, è necessario eseguire un'operazione necessaria aggiuntiva.  
  
In questa procedura dettagliata, vengono eseguite le attività principali seguenti:  
  
-   [Creare il tipo DeploymentPlanExecutor del collaboratore alla distribuzione](#CreateDeploymentContributor)  
  
-   [Installare il collaboratore alla distribuzione](#InstallDeploymentContributor)  
  
-   [Testare il collaboratore alla distribuzione](#TestDeploymentContributor)  
  
## <a name="prerequisites"></a>Prerequisites  
Per completare questa procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   È necessario avere installata una versione di Visual Studio che includa SQL Server Data Tools (SSDT) e supporti lo sviluppo in C# o VB.  
  
-   È necessario disporre di un progetto SQL contenente oggetti SQL.  
  
-   Un'istanza di SQL Server a cui sia possibile distribuire un progetto di database.  
  
> [!NOTE]  
> Questa procedura dettagliata è destinata ad utenti che abbiano già familiarità con le funzionalità SQL di SSDT. È inoltre necessario che l'utente conosca i concetti di base di Visual Studio, ad esempio come creare una libreria di classi e come utilizzare l'editor di codice per aggiungere codice a una classe.  
  
## <a name="CreateDeploymentContributor"></a>Creare un collaboratore alla distribuzione  
Per creare un collaboratore alla distribuzione, è necessario effettuare le attività seguenti:  
  
-   Creare un progetto Libreria di classi e aggiungere i riferimenti richiesti.  
  
-   Definire una classe denominata DeploymentUpdateReportContributor che erediti da [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx).  
  
-   Eseguire l'override del metodo OnExecute.  
  
-   Aggiungere una classe helper privata.  
  
-   Compilare l'assembly risultante.  
  
#### <a name="to-create-a-class-library-project"></a>Per creare un progetto Libreria di classi  
  
1.  Creare un progetto libreria di classi di Visual Basic o Visual C# denominato MyDeploymentContributor.  
  
2.  Rinominare il file "Class1.cs" in "DeploymentUpdateReportContributor.cs".  
  
3.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi riferimento**.  
  
4.  Selezionare **System.ComponentModel.Composition** nella scheda Framework.  
  
5.  Aggiungere i riferimenti SQL richiesti: fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi riferimento**. Fare clic su **Sfoglia** e passare alla cartella **C:\Programmi (x86)\Microsoft SQL Server\110\DAC\Bin**. Scegliere le voci **Microsoft.SqlServer.Dac.dll**, **Microsoft.SqlServer.Dac.Extensions.dll** e **Microsoft.Data.Tools.Schema.Sql.dll**, fare clic su **Aggiungi** e quindi fare clic su **OK**.  
  
    Iniziare ad aggiungere codice alla classe.  
  
#### <a name="to-define-the-deploymentupdatereportcontributor-class"></a>Per definire la classe DeploymentUpdateReportContributor  
  
1.  Nell'editor del codice aggiornare il file DeploymentUpdateReportContributor.cs in modo che corrisponda alle istruzioni **using** seguenti:  
  
    ```csharp  
    using System;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using Microsoft.SqlServer.Dac.Deployment;  
    using Microsoft.SqlServer.Dac.Extensibility;  
    using Microsoft.SqlServer.Dac.Model;  
  
    ```  
  
2.  Aggiornare la definizione della classe in modo che corrisponda a quanto segue:  
  
    ```csharp  
    /// <summary>  
        /// An executor that generates a report detailing the steps in the deployment plan. Will only run  
        /// if a "GenerateUpdateReport=true" contributor argument is set in the project file, in a targets file or  
        /// passed as an additional argument to the DacServices API. To set in a project file, add the following:  
        ///   
        /// <PropertyGroup>  
        ///     <ContributorArguments Condition="'$(Configuration)' == 'Debug'">  
        /// $(ContributorArguments);DeploymentUpdateReportContributor.GenerateUpdateReport=true;  
        ///     </ContributorArguments>  
        /// <PropertyGroup>  
        ///   
        /// </summary>  
        [ExportDeploymentPlanExecutor("MyDeploymentContributor.DeploymentUpdateReportContributor", "1.0.0.0")]  
        public class DeploymentUpdateReportContributor : DeploymentPlanExecutor  
        {  
        }  
  
    ```  
  
    È stato definito il collaboratore alla distribuzione che eredita da DeploymentPlanExecutor. Durante i processi di compilazione e distribuzione, i collaboratori personalizzati vengono caricati da una directory di estensioni standard. I collaboratori all'esecuzione del piano di distribuzione sono identificati da un attributo [ExportDeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.exportdeploymentplanexecutorattribute.aspx).  
  
    Questo attributo è richiesto per consentire di individuare i collaboratori. Dovrebbe essere simile a quanto riportato di seguito:  
  
    ```csharp  
    [ExportDeploymentPlanExecutor("MyDeploymentContributor.DeploymentUpdateReportContributor", "1.0.0.0")]  
  
    ```  
  
    In questo caso il primo parametro all'attributo deve essere un identificatore univoco, che verrà usato per identificare il collaboratore nei file del progetto. È consigliabile combinare lo spazio dei nomi della libreria (in questa procedura dettagliata MyDeploymentContributor) con il nome della classe (in questa procedura dettagliata DeploymentUpdateReportContributor), per produrre l'identificatore.  
  
3.  Successivamente, aggiungere il membro seguente che verrà utilizzato per consentire al provider di accettare un parametro della riga di comando:  
  
    ```csharp  
    public const string GenerateUpdateReport = "DeploymentUpdateReportContributor.GenerateUpdateReport";  
    ```  
  
    Questo membro consente all'utente di specificare se il report deve essere generato utilizzando l'opzione GenerateUpdateReport.  
  
    Quindi, eseguire l'override del metodo OnExecute per aggiungere il codice che si desidera eseguire quando viene distribuito un progetto di database.  
  
#### <a name="to-override-onexecute"></a>Per eseguire l'override di OnExecute  
  
-   Aggiungere il metodo seguente alla classe DeploymentUpdateReportContributor:  
  
    ```csharp  
    /// <summary>  
            /// Override the OnExecute method to perform actions when you execute the deployment plan for  
            /// a database project.  
            /// </summary>  
            protected override void OnExecute(DeploymentPlanContributorContext context)  
            {  
                // determine whether the user specified a report is to be generated  
                bool generateReport = false;  
                string generateReportValue;  
                if (context.Arguments.TryGetValue(GenerateUpdateReport, out generateReportValue) == false)  
                {  
                    // couldn't find the GenerateUpdateReport argument, so do not generate  
                    generateReport = false;  
                }  
                else  
                {  
                    // GenerateUpdateReport argument was specified, try to parse the value  
                    if (bool.TryParse(generateReportValue, out generateReport))  
                    {  
                        // if we end up here, the value for the argument was not valid.  
                        // default is false, so do nothing.  
                    }  
                }  
  
                if (generateReport == false)  
                {  
                    // if user does not want to generate a report, we are done  
                    return;  
                }  
  
                // We will output to the same directory where the deployment script  
                // is output or to the current directory  
                string reportPrefix = context.Options.TargetDatabaseName;  
                string reportPath;  
                if (string.IsNullOrEmpty(context.DeploymentScriptPath))  
                {  
                    reportPath = Environment.CurrentDirectory;  
                }  
                else  
                {  
                    reportPath = Path.GetDirectoryName(context.DeploymentScriptPath);  
                }  
                FileInfo summaryReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".summary.xml"));  
                FileInfo detailsReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".details.xml"));  
  
                // Generate the reports by using the helper class DeploymentReportWriter  
                DeploymentReportWriter writer = new DeploymentReportWriter(context);  
                writer.WriteReport(summaryReportFile);  
                writer.IncludeScripts = true;  
                writer.WriteReport(detailsReportFile);  
  
                string msg = "Deployment reports ->"  
                    + Environment.NewLine + summaryReportFile.FullName  
                    + Environment.NewLine + detailsReportFile.FullName;  
  
                ExtensibilityError reportMsg = new ExtensibilityError(msg, Severity.Message);  
                base.PublishMessage(reportMsg);  
            }  
        /// <summary>  
        /// Override the OnExecute method to perform actions when you execute the deployment plan for  
        /// a database project.  
        /// </summary>  
            protected override void OnExecute(DeploymentPlanContributorContext context)  
            {  
                // determine whether the user specified a report is to be generated  
                bool generateReport = false;  
                string generateReportValue;  
                if (context.Arguments.TryGetValue(GenerateUpdateReport, out generateReportValue) == false)  
                {  
                    // couldn't find the GenerateUpdateReport argument, so do not generate  
                    generateReport = false;  
                }  
                else  
                {  
                    // GenerateUpdateReport argument was specified, try to parse the value  
                    if (bool.TryParse(generateReportValue, out generateReport))  
                    {  
                        // if we end up here, the value for the argument was not valid.  
                        // default is false, so do nothing.  
                    }  
                }  
  
                if (generateReport == false)  
                {  
                    // if user does not want to generate a report, we are done  
                    return;  
                }  
  
                // We will output to the same directory where the deployment script  
                // is output or to the current directory  
                string reportPrefix = context.Options.TargetDatabaseName;  
                string reportPath;  
                if (string.IsNullOrEmpty(context.DeploymentScriptPath))  
                {  
                    reportPath = Environment.CurrentDirectory;  
                }  
                else  
                {  
                    reportPath = Path.GetDirectoryName(context.DeploymentScriptPath);  
                }  
                FileInfo summaryReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".summary.xml"));  
                FileInfo detailsReportFile = new FileInfo(Path.Combine(reportPath, reportPrefix + ".details.xml"));  
  
                // Generate the reports by using the helper class DeploymentReportWriter  
                DeploymentReportWriter writer = new DeploymentReportWriter(context);  
                writer.WriteReport(summaryReportFile);  
                writer.IncludeScripts = true;  
                writer.WriteReport(detailsReportFile);  
  
                string msg = "Deployment reports ->"  
                    + Environment.NewLine + summaryReportFile.FullName  
                    + Environment.NewLine + detailsReportFile.FullName;  
  
                DataSchemaError reportMsg = new DataSchemaError(msg, ErrorSeverity.Message);  
                base.PublishMessage(reportMsg);  
            }  
    ```  
  
    Al metodo OnExecute viene passato un oggetto [DeploymentPlanContributorContext](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplancontributorcontext.aspx) che fornisce accesso a qualsiasi argomento specificato, al modello di database di origine e di destinazione, alle proprietà di compilazione e ai file di estensione. In questo esempio viene ottenuto il modello e vengono chiamate le funzioni helper per restituire informazioni sul modello. Viene utilizzato il metodo helper PublishMessage sulla classe di base per segnalare gli eventuali errori che si verificano.  
  
    I tipi e i metodi aggiuntivi di interesse includono: [TSqlModel](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlmodel.aspx), [ModelComparisonResult](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.modelcomparisonresult.aspx), [DeploymentPlanHandle](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanhandle.aspx) e [SqlDeploymentOptions](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqldeploymentoptions.aspx).  
  
    Successivamente, si definisce una classe helper che accede ai dettagli del piano di distribuzione.  
  
#### <a name="to-add-the-helper-class-that-generates-the-report-body"></a>Per aggiungere la classe helper che genera il corpo del report  
  
-   Aggiungere la classe helper e i metodi relativi aggiungendo il codice seguente:  
  
    ```csharp  
    /// <summary>  
            /// This class is used to generate a deployment  
            /// report.   
            /// </summary>  
            private class DeploymentReportWriter  
            {  
                readonly TSqlModel _sourceModel;  
                readonly ModelComparisonResult _diff;  
                readonly DeploymentStep _planHead;  
  
                /// <summary>  
                /// The constructor accepts the same context info  
                /// that was passed to the OnExecute method of the  
                /// deployment contributor.  
                /// </summary>  
                public DeploymentReportWriter(DeploymentPlanContributorContext context)  
                {  
                    if (context == null)  
                    {  
                        throw new ArgumentNullException("context");  
                    }  
  
                    // save the source model, source/target differences,  
                    // and the beginning of the deployment plan.  
                    _sourceModel = context.Source;  
                    _diff = context.ComparisonResult;  
                    _planHead = context.PlanHandle.Head;  
                }  
                /// <summary>  
                /// Property indicating whether script bodies  
                /// should be included in the report.  
                /// </summary>  
                public bool IncludeScripts { get; set; }  
  
                /// <summary>  
                /// Drives the report generation, opening files,   
                /// writing the beginning and ending report elements,  
                /// and calling helper methods to report on the  
                /// plan operations.  
                /// </summary>  
                internal void WriteReport(FileInfo reportFile)  
                {// Assumes that we have a valid report file  
                    if (reportFile == null)  
                    {  
                        throw new ArgumentNullException("reportFile");  
                    }  
  
                    // set up the XML writer  
                    XmlWriterSettings xmlws = new XmlWriterSettings();  
                    // Indentation makes it a bit more readable  
                    xmlws.Indent = true;  
                    FileStream fs = new FileStream(reportFile.FullName, FileMode.Create, FileAccess.Write, FileShare.ReadWrite);  
                    XmlWriter xmlw = XmlWriter.Create(fs, xmlws);  
  
                    try  
                    {  
                        xmlw.WriteStartDocument(true);  
                        xmlw.WriteStartElement("DeploymentReport");  
  
                        // Summary report of the operations that  
                        // are contained in the plan.  
                        ReportPlanOperations(xmlw);  
  
                        // You could add a method call here  
                        // to produce a detailed listing of the   
                        // differences between the source and  
                        // target model.  
                        xmlw.WriteEndElement();  
                        xmlw.WriteEndDocument();  
                        xmlw.Flush();  
                        fs.Flush();  
                    }  
                    finally  
                    {  
                        xmlw.Close();  
                        fs.Dispose();  
                    }  
                }  
  
                /// <summary>  
                /// Writes details for the various operation types  
                /// that could be contained in the deployment plan.  
                /// Optionally writes script bodies, depending on  
                /// the value of the IncludeScripts property.  
                /// </summary>  
                private void ReportPlanOperations(XmlWriter xmlw)  
                {// write the node to indicate the start  
                    // of the list of operations.  
                    xmlw.WriteStartElement("Operations");  
  
                    // Loop through the steps in the plan,  
                    // starting at the beginning.  
                    DeploymentStep currentStep = _planHead;  
                    while (currentStep != null)  
                    {  
                        // Report the type of step  
                        xmlw.WriteStartElement(currentStep.GetType().Name);  
  
                        // based on the type of step, report  
                        // the relevant information.  
                        // Note that this procedure only handles   
                        // a subset of all step types.  
                        if (currentStep is SqlRenameStep)  
                        {  
                            SqlRenameStep renameStep = (SqlRenameStep)currentStep;  
                            xmlw.WriteAttributeString("OriginalName", renameStep.OldName);  
                            xmlw.WriteAttributeString("NewName", renameStep.NewName);  
                            xmlw.WriteAttributeString("Category", GetElementCategory(renameStep.RenamedElement));  
                        }  
                        else if (currentStep is SqlMoveSchemaStep)  
                        {  
                            SqlMoveSchemaStep moveStep = (SqlMoveSchemaStep)currentStep;  
                            xmlw.WriteAttributeString("OrignalName", moveStep.PreviousName);  
                            xmlw.WriteAttributeString("NewSchema", moveStep.NewSchema);  
                            xmlw.WriteAttributeString("Category", GetElementCategory(moveStep.MovedElement));  
                        }  
                        else if (currentStep is SqlTableMigrationStep)  
                        {  
                            SqlTableMigrationStep dmStep = (SqlTableMigrationStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(dmStep.SourceTable));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(dmStep.SourceElement));  
                        }  
                        else if (currentStep is CreateElementStep)  
                        {  
                            CreateElementStep createStep = (CreateElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(createStep.SourceElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(createStep.SourceElement));  
                        }  
                        else if (currentStep is AlterElementStep)  
                        {  
                            AlterElementStep alterStep = (AlterElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(alterStep.SourceElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(alterStep.SourceElement));  
                        }  
                        else if (currentStep is DropElementStep)  
                        {  
                            DropElementStep dropStep = (DropElementStep)currentStep;  
                            xmlw.WriteAttributeString("Name", GetElementName(dropStep.TargetElement));  
                            xmlw.WriteAttributeString("Category", GetElementCategory(dropStep.TargetElement));  
                        }  
  
                        // If the script bodies are to be included,  
                        // add them to the report.  
                        if (this.IncludeScripts)  
                        {  
                            using (StringWriter sw = new StringWriter())  
                            {  
                                currentStep.GenerateBatchScript(sw);  
                                string tsqlBody = sw.ToString();  
                                if (string.IsNullOrEmpty(tsqlBody) == false)  
                                {  
                                    xmlw.WriteCData(tsqlBody);  
                                }  
                            }  
                        }  
  
                        // close off the current step  
                        xmlw.WriteEndElement();  
                        currentStep = currentStep.Next;  
                    }  
                    xmlw.WriteEndElement();  
                }  
  
                /// <summary>  
                /// Returns the category of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementCategory(TSqlObject element)  
                {  
                    return element.ObjectType.Name;  
                }  
  
                /// <summary>  
                /// Returns the name of the specified element  
                /// in the source model  
                /// </summary>  
                private static string GetElementName(TSqlObject element)  
                {  
                    StringBuilder name = new StringBuilder();  
                    if (element.Name.HasExternalParts)  
                    {  
                        foreach (string part in element.Name.ExternalParts)  
                        {  
                            if (name.Length > 0)  
                            {  
                                name.Append('.');  
                            }  
                            name.AppendFormat("[{0}]", part);  
                        }  
                    }  
  
                    foreach (string part in element.Name.Parts)  
                    {  
                        if (name.Length > 0)  
                        {  
                            name.Append('.');  
                        }  
                        name.AppendFormat("[{0}]", part);  
                    }  
  
                    return name.ToString();  
                }  
            }        /// <summary>  
            /// This class is used to generate a deployment  
            /// report.   
            /// </summary>  
            private class DeploymentReportWriter  
            {  
                /// <summary>  
                /// The constructor accepts the same context info  
                /// that was passed to the OnExecute method of the  
                /// deployment contributor.  
                /// </summary>  
                public DeploymentReportWriter(DeploymentPlanContributorContext context)  
                {  
               }  
                /// <summary>  
                /// Property indicating whether script bodies  
                /// should be included in the report.  
                /// </summary>  
                public bool IncludeScripts { get; set; }  
  
                /// <summary>  
                /// Drives the report generation, opening files,   
                /// writing the beginning and ending report elements,  
                /// and calling helper methods to report on the  
                /// plan operations.  
                /// </summary>  
                internal void WriteReport(FileInfo reportFile)  
                {  
                }  
  
                /// <summary>  
                /// Writes details for the various operation types  
                /// that could be contained in the deployment plan.  
                /// Optionally writes script bodies, depending on  
                /// the value of the IncludeScripts property.  
                /// </summary>  
                private void ReportPlanOperations(XmlWriter xmlw)  
                {  
                }  
  
                /// <summary>  
                /// Returns the category of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementCategory(IModelElement element)  
                {  
                }  
  
                /// <summary>  
                /// Returns the name of the specified element  
                /// in the source model  
                /// </summary>  
                private string GetElementName(IModelElement element)  
                {  
                }  
            }  
    ```  
  
-   Salvare le modifiche apportate al file della classe. Nella classe helper viene fatto riferimento a una serie di tipi utili:  
  
    |**Area di codice**|**Tipi utili**|  
    |-----------------|--------------------|  
    |Membri di classe|[TSqlModel](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlmodel.aspx), [ModelComparisonResult](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.modelcomparisonresult.aspx), [DeploymentStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentstep.aspx)|  
    |Metodo WriteReport|XmlWriter e XmlWriterSettings|  
    |Metodo ReportPlanOperations|I tipi di interesse includono i seguenti: [DeploymentStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentstep.aspx), [SqlRenameStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqlrenamestep.aspx), [SqlMoveSchemaStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqlmoveschemastep.aspx), [SqlTableMigrationStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.sqltablemigrationstep.aspx), [CreateElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.createelementstep.aspx), [AlterElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.alterelementstep.aspx), [DropElementStep](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.dropelementstep.aspx).<br /><br />Esistono alcuni altri passaggi. Per un elenco completo, vedere la documentazione dell'API.|  
    |GetElementCategory|[TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx)|  
    |GetElementName|[TSqlObject](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.model.tsqlobject.aspx)|  
  
    Compilare la libreria di classi.  
  
#### <a name="to-sign-and-build-the-assembly"></a>Per firmare e compilare l'assembly  
  
1.  Scegliere **Proprietà di MyDeploymentContributor** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Firma** .  
  
3.  Fare clic su **Firma assembly**.  
  
4.  In **Scegli un file chiave con nome sicuro** fare clic su **<New>**.  
  
5.  Nella finestra di dialogo **Crea chiave con nome sicuro** , in **Nome file di chiave**, digitare **MyRefKey**.  
  
6.  (facoltativo) È possibile specificare una password per il file di chiave con nome sicuro.  
  
7.  Fare clic su **OK**.  
  
8.  Scegliere **Salva tutti** dal menu **File**.  
  
9. Scegliere **Compila soluzione** dal menu **Compila**.  
  
È quindi necessario installare l'assembly in modo che venga caricato quando si compilano e distribuiscono progetti SQL.  
  
## <a name="InstallDeploymentContributor"></a>Installare un collaboratore alla distribuzione  
Per installare un collaboratore alla distribuzione, è necessario copiare l'assembly e il file con estensione pdb associato nella cartella Extensions.  
  
#### <a name="to-install-the-mydeploymentcontributor-assembly"></a>Per installare l'assembly MyDeploymentContributor  
  
-   Nella prossima esercitazione verrà illustrato come copiare le informazioni sull'assembly nella directory Estensioni. Quando si avvia Visual Studio, le estensioni vengono identificate nella directory %Programmi%\Microsoft SQL Server\110\DAC\Bin\Extensions e relative sottodirectory, quindi vengono rese disponibili per l'utilizzo:  
  
-   Copiare il file di assembly **MyDeploymentContributor.dll** dalla directory di output alla directory %Programmi%\Microsoft SQL Server\110\DAC\Bin\Extensions. Per impostazione predefinita, il percorso del file con estensione dll compilato è PercorsoSoluzione\PercorsoProgetto\bin\Debug o PercorsoSoluzione\PercorsoProgetto\bin\Release.  
  
## <a name="TestDeploymentContributor"></a>Testare il collaboratore alla distribuzione  
Per testare il collaboratore alla distribuzione, è necessario effettuare le attività seguenti:  
  
-   Aggiungere proprietà al file con estensione sqlproj che si intende distribuire.  
  
-   Distribuire il progetto utilizzando MSBuild e fornendo il parametro appropriato.  
  
### <a name="add-properties-to-the-sql-project-sqlproj-file"></a>Aggiungere proprietà al file del progetto SQL (.sqlproj)  
È necessario aggiornare sempre il file del progetto SQL per specificare l'ID dei collaboratori che si desidera eseguire. Inoltre, poiché questo collaboratore prevede un argomento "GenerateUpdateReport", è necessario specificarlo come argomento del collaboratore.  
  
Questa operazione può essere eseguita in due modi. È possibile modificare manualmente il file con estensione sqlproj per aggiungere gli argomenti richiesti. È possibile scegliere di eseguire questa operazione se il collaboratore non contiene gli argomenti del collaboratore necessari per la configurazione o se non si prevede di riutilizzare il collaboratore in molti progetti. Se si sceglie questa opzione, aggiungere le istruzioni seguenti nel file con estensione sqlproj dopo il primo nodo Import nel file:  
  
```  
<PropertyGroup>  
    <DeploymentContributors>$(DeploymentContributors); MyDeploymentContributor.DeploymentUpdateReportContributor</DeploymentContributors>  
<ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments);DeploymentUpdateReportContributor.GenerateUpdateReport=true;</ContributorArguments>  
  </PropertyGroup>  
```  
  
Il secondo metodo consiste nel creare un file targets contenente gli argomenti del collaboratore richiesti. È utile se si utilizza lo stesso collaboratore per più progetti e si dispone degli argomenti del collaboratore richiesti, dal momento che include i valori predefiniti. In questo caso, creare un file targets nel percorso delle estensioni MSBuild.  
  
1.  Passare a %Programmi%\MSBuild.  
  
2.  Creare una nuova cartella "MyContributors" in cui archiviare i file TARGETS.  
  
3.  Creare un nuovo file "MyContributors.targets" in questa directory, aggiungere il testo seguente e salvare il file:  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
  
    <Project xmlns="https://schemas.microsoft.com/developer/msbuild/2003">  
      <PropertyGroup>  
    <DeploymentContributors>$(DeploymentContributors);MyDeploymentContributor.DeploymentUpdateReportContributor</DeploymentContributors>  
    <ContributorArguments Condition="'$(Configuration)' == 'Debug'">$(ContributorArguments); DeploymentUpdateReportContributor.GenerateUpdateReport=true;</ContributorArguments>  
      </PropertyGroup>  
    </Project>  
    ```  
  
4.  Nel file con estensione sqlproj per qualsiasi progetto per cui si vogliono eseguire collaboratori, importare il file targets aggiungendo l'istruzione seguente al file sqlproj dopo il nodo \<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v$(VisualStudioVersion)\SSDT\Microsoft.Data.Tools.Schema.SqlTasks.targets" \/> nel file:  
  
    ```  
    <Import Project="$(MSBuildExtensionsPath)\MyContributors\MyContributors.targets " />  
    ```  
  
Dopo aver seguito uno di questi approcci, è possibile utilizzare MSBuild per passare i parametri per compilazioni della riga di comando.  
  
> [!NOTE]  
> È necessario aggiornare sempre la proprietà "DeploymentContributors" per specificare il proprio ID collaboratore. Si tratta dello stesso ID usato nell'attributo "ExportDeploymentPlanExecutor" nel file di origine del collaboratore. Senza questo il collaboratore non verrà eseguito durante la compilazione del progetto. La proprietà "ContributorArguments" deve essere aggiornata solo se si hanno argomenti richiesti per l'esecuzione del collaboratore.  
  
### <a name="deploy-the-database-project"></a>Distribuire il progetto di database  
Il progetto può essere pubblicato o distribuito normalmente in Visual Studio. È sufficiente aprire una soluzione contenente il progetto SQL e scegliere l'opzione "Pubblica..." dal menu di scelta rapida per il progetto o usare F5 per una distribuzione di debug in Local DB. In questo esempio verrà usata la finestra di dialogo "Pubblica..." per generare uno script di distribuzione.  
  
##### <a name="to-deploy-your-sql-project-and-generate-a-deployment-report"></a>Per distribuire il progetto SQL e generare un report di distribuzione  
  
1.  Aprire Visual Studio e aprire la soluzione che contiene il progetto SQL.  
  
2.  Selezionare il progetto e premere "F5" per eseguire una distribuzione di debug. Nota: poiché l'elemento ContributorArguments è impostato solo per essere incluso se la configurazione è "Debug", per ora il report della distribuzione viene generato solo per le distribuzioni di debug. Per modificare questo, rimuovere l'istruzione Condition="'$(Configuration)' == 'Debug'" dalla definizione ContributorArguments.  
  
3.  Nella finestra di output viene visualizzato un output simile al seguente:  
  
    ```  
    ------ Deploy started: Project: Database1, Configuration: Debug Any CPU ------  
    Finished verifying cached model in 00:00:00  
    Deployment reports ->  
  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyTargetDatabase.summary.xml  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyTargetDatabase.details.xml  
  
      Deployment script generated to:  
      C:\Users\UserName\Documents\Visual Studio 2012\Projects\MyDatabaseProject\MyDatabaseProject\sql\debug\MyDatabaseProject.sql  
  
    ```  
  
4.  Aprire MyTargetDatabase.summary.xml ed esaminarne il contenuto. Il file è simile all'esempio seguente che mostra la distribuzione di un nuovo database:  
  
    ```  
    <?xml version="1.0" encoding="utf-8" standalone="yes"?>  
    <DeploymentReport>  
      <Operations>  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <BeginPreDeploymentScriptStep />  
        <DeploymentScriptStep />  
        <EndPreDeploymentScriptStep />  
        <SqlBeginPreservationStep />  
        <SqlEndPreservationStep />  
        <SqlBeginDropsStep />  
        <SqlEndDropsStep />  
        <SqlBeginAltersStep />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales" Category="Schema" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Customer" Category="Table" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.PK_Customer_CustID" Category="Primary Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Orders" Category="Table" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.PK_Orders_OrderID" Category="Primary Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Customer_YTDOrders" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Customer_YTDSales" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Orders_OrderDate" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.Def_Orders_Status" Category="Default Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.FK_Orders_Customer_CustID" Category="Foreign Key" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.CK_Orders_FilledDate" Category="Check Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.CK_Orders_OrderDate" Category="Check Constraint" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspCancelOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspFillOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspNewCustomer" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspPlaceNewOrder" Category="Procedure" />  
        <SqlPrintStep />  
        <CreateElementStep Name="Sales.uspShowOrderDetails" Category="Procedure" />  
        <SqlEndAltersStep />  
        <DeploymentScriptStep />  
        <BeginPostDeploymentScriptStep />  
        <DeploymentScriptStep />  
        <EndPostDeploymentScriptStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
        <DeploymentScriptDomStep />  
      </Operations>  
    </DeploymentReport>  
  
    ```  
  
    > [!NOTE]  
    > Se si distribuisce un progetto di database identico al database di destinazione, il report risultante non sarà molto significativo. Per risultati più significativi, distribuire modifiche a un database o distribuire un nuovo database.  
  
5.  Aprire MyTargetDatabase.details.xml ed esaminarne il contenuto. Una piccola sezione del file di dettagli mostra le voci e lo script che creano lo schema Sales, che stampano un messaggio sulla creazione di una tabella e che creano la tabella:  
  
    ```  
    <CreateElementStep Name="Sales" Category="Schema"><![CDATA[CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
  
    ]]></CreateElementStep>  
        <SqlPrintStep><![CDATA[PRINT N'Creating [Sales].[Customer]...';  
  
    ]]></SqlPrintStep>  
        <CreateElementStep Name="Sales.Customer" Category="Table"><![CDATA[CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
  
    ]]></CreateElementStep>  
  
    ```  
  
    Analizzando il piano di distribuzione quando viene eseguito, è possibile segnalare qualsiasi informazione contenuta nella distribuzione ed è possibile eseguire interventi aggiuntivi basati sui passaggi del piano.  
  
## <a name="next-steps"></a>Next Steps  
È possibile creare strumenti aggiuntivi per eseguire l'elaborazione dei file XML di output. Questo è solo un esempio di [DeploymentPlanExecutor](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanexecutor.aspx). È anche possibile creare un elemento [DeploymentPlanModifier](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.deployment.deploymentplanmodifier.aspx) per modificare un piano di distribuzione prima che sia eseguito.  
  
## <a name="see-also"></a>Vedere anche  
[Procedura dettagliata: Estendere la compilazione del progetto del database per generare statistiche del modello](https://msdn.microsoft.com/library/ee461508(v=vs.100).aspx)  
[Procedura dettagliata: estendere la distribuzione del progetto di database per modificare il piano di distribuzione](https://msdn.microsoft.com/library/ee461507(v=vs.100).aspx)  
[Personalizzare la compilazione e la distribuzione del database tramite collaboratori alla compilazione e distribuzione](https://msdn.microsoft.com/library/ee461505(v=vs.100).aspx)  
  
