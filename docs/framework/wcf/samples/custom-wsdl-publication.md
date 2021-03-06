---
title: Vlastní publikování WSDL
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 725b62a26d640e242010a01ff810ea90d5cc53bc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508417"
---
# <a name="custom-wsdl-publication"></a>Vlastní publikování WSDL
Tato ukázka předvádí, jak:  
  
-   Implementace <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> na vlastní <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> atribut exportujte vlastnosti atribut jako poznámky WSDL.  
  
-   Implementace <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> Import vlastního WSDL poznámky.  
  
-   Implementace <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> na vlastní smlouvy chování a chování vlastní operace, jako komentáře v CodeDom pro importované kontrakt a operace zápisu importované poznámky.  
  
-   Použití <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> stáhnout WSDL, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> pro import WSDL, pomocí vlastní import WSDL a <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> ke generování kódu klienta Windows Communication Foundation (WCF) s poznámkami WSDL jako / / / / / a "" komentáře v jazyce C# a Visual Základní.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="service"></a>Služba  
 Služba v této ukázce je označena pomocí dvou vlastních atributů. První, `WsdlDocumentationAttribute`, přijímá řetězec v konstruktoru a lze použít k poskytování rozhraní kontraktu nebo operaci s řetězcem, který popisuje jeho využití. Druhá s názvem `WsdlParamOrReturnDocumentationAttribute`, lze použít k vrácení hodnoty nebo parametry popisují tyto hodnoty v operaci. Následující příklad ukazuje, kontrakt služby `ICalculator`, které jsou popsány pomocí těchto atributů.  
  
```  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 `WsdlDocumentationAttribute` Implementuje <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior>, takže instance atributu jsou přidány do odpovídajících <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Description.OperationDescription> při otevření služby. Atribut také implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension>. Když <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> je volána, <xref:System.ServiceModel.Description.WsdlExporter> , který slouží k exportu metadat a <xref:System.ServiceModel.Description.WsdlContractConversionContext> , která obsahuje popis služby, objekty jsou předány v jako parametry umožňující úpravy exportované metadat.  
  
 V této ukázce, podle toho, jestli se má kontext objekt exportu <xref:System.ServiceModel.Description.ContractDescription> nebo <xref:System.ServiceModel.Description.OperationDescription>, komentáře se extrahují z atributů pomocí vlastnosti text a je přidán do elementu anotace WSDL, jak je znázorněno v následujícím kódu.  
  
```  
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (contractDescription != null)  
    {  
        // Inside this block it is the contract-level comment attribute.  
        // This.Text returns the string for the contract attribute.  
        // Set the doc element; if this isn't done first, there is no XmlElement in the   
        // DocumentElement property.  
        context.WsdlPortType.Documentation = string.Empty;  
        // Contract comments.  
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;  
        XmlElement summaryElement = owner.CreateElement("summary");  
        summaryElement.InnerText = this.Text;  
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);  
    }  
    else  
    {  
        Operation operation = context.GetOperation(operationDescription);  
        if (operation != null)  
        {  
            // We are dealing strictly with the operation here.  
            // This.Text returns the string for the operation-level attributes.  
            // Set the doc element; if this isn't done first, there is no XmlElement in the   
            // DocumentElement property.  
            operation.Documentation = String.Empty;  
  
            // Operation C# triple comments.  
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;  
            XmlElement newSummaryElement = owner.CreateElement("summary");  
            newSummaryElement.InnerText = this.Text;  
            operation.DocumentationElement.AppendChild(newSummaryElement);  
```  
  
 Pokud operace se exportuje, ukázka používá reflexi získat žádné `WsdlParamOrReturnDocumentationAttribute` hodnoty parametrů a vrácených hodnot a přidá je do elementů poznámky WSDL pro danou operaci následujícím způsobem.  
  
```  
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 Ukázka pak publikuje metadata ve standardním způsobem pomocí následující konfigurační soubor.  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a>Svcutil klienta  
 Tato ukázka nepoužívá Svcutil.exe. Smlouva je k dispozici v generatedClient.cs souboru tak, že po vzorek ukazuje, import vlastního WSDL a generování kódu, služba může být vyvolána. Pokud chcete používat pro účely tohoto příkladu následující Import vlastního WSDL, můžete spustit Svcutil.exe a zadejte `/svcutilConfig` možnost poskytne cestu k souboru konfigurace klienta používané v tomto příkladu, který odkazuje `WsdlDocumentation.dll` knihovny. Načíst `WsdlDocumentationImporter`, však musí mít možnost pro vyhledání a načtení Svuctil.exe `WsdlDocumentation.dll` knihovny, což znamená, že buď, který je zaregistrován v globální mezipaměti sestavení, v cestě, nebo je ve stejném adresáři jako Svcutil.exe. Základní ukázka takovou situaci, je nejjednodušší krokem je ke kopírování Svcutil.exe a konfigurační soubor klienta do stejného adresáře jako `WsdlDocumentation.dll` a spustit ho odtud.  
  
## <a name="the-custom-wsdl-importer"></a>Import vlastního WSDL  
 Vlastní <xref:System.ServiceModel.Description.IWsdlImportExtension> objekt `WsdlDocumentationImporter` také implementuje <xref:System.ServiceModel.Description.IContractBehavior> a <xref:System.ServiceModel.Description.IOperationBehavior> přidávaného do importované koncové body ServiceEndpoints znamenají a <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> má být volána k úpravě generování kódu při kontrakt a operace vytváří se kód.  
  
 V první <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> metoda, ukázka Určuje, zda je na úrovni smlouvy nebo operace WSDL poznámky a přidá sama jako chování v příslušné oboru předávání text poznámky importovaných do konstruktoru.  
  
```  
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 Potom při generování kódu, systém vyvolá <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> a <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> metody předávání informací o vhodném kontextu. Ukázka formáty vlastního WSDL poznámky a vloží je do CodeDom jako komentáře.  
  
```  
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a>Klientská aplikace  
 Klientská aplikace načte Import vlastního WSDL tak, že zadáte v konfiguračním souboru aplikace.  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 Jakmile byl zadán vlastní tabulkách, načte metadata systém WCF vlastního programu pro import do libovolného <xref:System.ServiceModel.Description.WsdlImporter> vytvořeném pro tento účel. Tento příklad používá <xref:System.ServiceModel.Description.MetadataExchangeClient> stáhnout metadata a <xref:System.ServiceModel.Description.WsdlImporter> správně nakonfigurovaný pro import metadat pomocí vlastní Importér vzorovým kódem se vytvoří, a <xref:System.ServiceModel.Description.ServiceContractGenerator> změněné smlouvy informace do obou jazyka Visual Basic a C# klientský kód, který lze použít v sadě Visual Studio pro podporu technologie Intellisense nebo zkompilovány do dokumentace XML.  
  
```  
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a>Viz také
