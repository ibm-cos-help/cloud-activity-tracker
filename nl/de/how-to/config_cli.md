---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-22"

keywords: IBM Cloud, Activity Tracker, config CLI

subcollection: cloud-activity-tracker

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:codeblock: .codeblock}
{:tip: .tip}
{:download: .download}
{:important: .important}
{:note: .note}


# Activity Tracker-CLI konfigurieren
{: #config_cli}

Der {{site.data.keyword.cloudaccesstraillong}}-Service enthält eine Befehlszeilenschnittstelle (CLI - Command-Line Interface), mit der Sie Ihre Ereignisse in der Cloud verwalten können. Mit dem {{site.data.keyword.cloud_notm}}-Plug-in können Sie den Status der Ereignisse anzeigen, Ereignisse herunterladen und die Aufbewahrungsrichtlinie konfigurieren. Die CLI bietet verschiedene Typen von Hilfe an: allgemeine Hilfe für die CLI und die unterstützten Befehle, Hilfe für Befehle mit Informationen zur Verwendung eines Befehls sowie Hilfe für Unterbefehle mit Informationen zur Verwendung eines Unterbefehls für einen Befehl.
{:shortdesc}


## {{site.data.keyword.cloudaccesstrailshort}}-Plug-in über das {{site.data.keyword.cloud_notm}}-Repository installieren
{: #install_cli_repo}

Führen Sie die folgenden Schritte aus, um die {{site.data.keyword.cloudaccesstrailshort}}-CLI zu installieren:

1. Installieren Sie die {{site.data.keyword.cloud_notm}}-CLI.

   Weitere Informationen finden Sie in [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle (CLI) installieren](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).
   
2. Ermitteln Sie den Namen des Plug-ins im Repository. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud plugin repo-plugins
    ```
    {: codeblock}
    
    Der Name des Plug-ins lautet **activity-tracker**. 

3. Installieren Sie das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud plugin install activity-tracker -r Bluemix
    ```
    {: codeblock}
 
4. Überprüfen Sie, ob das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in installiert wurde. 
  
    Führen Sie zum Beispiel den folgenden Befehl aus, um eine Liste der installierten Plug-ins abzurufen:
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## {{site.data.keyword.cloudaccesstrailshort}}-Plug-in mithilfe einer Datei installieren
{: #install_cli}

Führen Sie die folgenden Schritte aus, um die {{site.data.keyword.cloudaccesstrailshort}}-CLI zu installieren:

1. Installieren Sie die {{site.data.keyword.cloud_notm}}-CLI.

   Weitere Informationen finden Sie in [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle (CLI) installieren](/docs/cli?topic=cloud-cli-ibmcloud-cli#ibmcloud-cli).

2. Installieren Sie das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in. 

    * Informationen zu Linux finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Linux installieren](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_linux). 
    * Informationen zu Windows finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Windows installieren](/docs/services/cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_windows). 
    * Informationen zu Mac OS X finden Sie in [{{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Mac OS X installieren](/docs/services//cloud-activity-tracker/how-to?topic=cloud-activity-tracker-config_cli#install_cli_mac). 
 
3. Überprüfen Sie die Installation des CLI-Plug-ins. 
  
    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie den folgenden Befehl aus: 
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    


## {{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Linux mithilfe einer Datei installieren
{: #install_cli_linux}

Führen Sie die folgenden Schritte aus, um das Plug-in unter Linux zu installieren: 

1. Installieren Sie das Plug-in. 

    Laden Sie die aktuelle Version des Plug-ins für die CLI des {{site.data.keyword.cloudaccesstrailshort}}-Service (activity-tracker) von [der {{site.data.keyword.cloud_notm}}-CLI-Seite ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins){:new_window} herunter. 
	
	* Wählen Sie den folgenden Wert für die Plattform aus: **linux64**. 
	
	* Klicken Sie auf **Datei speichern**. 
    
2. Installieren Sie das Plug-in. Führen Sie den folgenden Befehl aus: 
        
    ```
    ibmcloud plugin install -f activity-tracker-linux-amd64-3.3.0
    ```
    {: codeblock}




## {{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Windows mithilfe einer Datei installieren
{: #install_cli_windows}

Führen Sie die folgenden Schritte aus, um das Plug-in unter Windows zu installieren: 

1. Laden Sie die aktuelle Version des Plug-ins für die CLI des {{site.data.keyword.cloudaccesstrailshort}}-Service (activity-tracker) von [der {{site.data.keyword.cloud_notm}}-CLI-Seite ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins){:new_window} herunter.  
	
	1. Wählen Sie den folgenden Wert für die Plattform aus: **win64**. 
	2. Klicken Sie auf **Datei speichern**.  
    
2. Installieren Sie das Plug-in. Führen Sie den folgenden Befehl aus: 
        
    ```
    ibmcloud plugin install -f activity-tracker-windows-amd64-3.3.0.exe
    ```
    {: codeblock}

	

## {{site.data.keyword.cloudaccesstrailshort}}-Plug-in unter Mac OS X mithilfe einer Datei installieren
{: #install_cli_mac}

Führen Sie die folgenden Schritte aus, um das Plug-in unter Mac OS X zu installieren: 

1. Laden Sie die aktuelle Version des Plug-ins für die CLI des {{site.data.keyword.cloudaccesstrailshort}}-Service (activity-tracker) von [der {{site.data.keyword.cloud_notm}}-CLI-Seite ![Symbol für externen Link](../../../icons/launch-glyph.svg "Symbol für externen Link")](https://clis.ng.bluemix.net/ui/repository.html#bluemix-plugins){:new_window} herunter. 
	
	1. Wählen Sie den folgenden Wert für die Plattform aus: `osx`.  
	2. Klicken Sie auf **Datei speichern**.  
    
2. Installieren Sie das Plug-in. Führen Sie den folgenden Befehl aus: 
        
    ```
    ibmcloud plugin install -f activity-tracker-darwin-amd64-3.3.0
    ```
    {: codeblock}

	
	
## {{site.data.keyword.cloudaccesstrailshort}}-CLI deinstallieren
{: #uninstall_cli}

Zum Deinstallieren der CLI löschen Sie das Plug-in.
{:shortdesc}

Führen Sie zum Deinstallieren der CLI für den {{site.data.keyword.cloudaccesstrailshort}}-Service die folgenden Schritte aus:

1. Überprüfen Sie, welche Version des CLI-Plug-ins installiert ist. 
  
    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie den folgenden Befehl aus: 
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    
2. Wenn das Plug-in installiert ist, führen Sie den Befehl `ibmcloud plugin uninstall` aus, um das CLI-Plug-in zu deinstallieren. 

    Führen Sie den folgenden Befehl aus: 
        
    ```
    ibmcloud plugin uninstall activity-tracker
    ```
    {: codeblock}
  

## {{site.data.keyword.cloudaccesstrailshort}}-CLI über das Repository aktualisieren
{: #update_cli}

Führen Sie zum Aktualisieren der CLI den Befehl *ibmcloud plugin update* aus.
{:shortdesc}

Führen Sie die folgenden Schritte aus, um die CLI für den {{site.data.keyword.cloudaccesstrailshort}}-Service zu aktualisieren:

1. Aktualisieren Sie das {{site.data.keyword.cloudaccesstrailshort}}-Plug-in. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud plugin update activity-tracker -r Bluemix
    ```
    {: codeblock}
 
2. Überprüfen Sie die Installation des CLI-Plug-ins. 
  
    Überprüfen Sie beispielsweise die Version des Plug-ins. Führen Sie den folgenden Befehl aus: 
    
    ```
    ibmcloud plugin list
    ```
    {: codeblock}
    





## Erweiterte Hilfe abrufen
{: #general_cli_help}

Führen Sie die folgenden Schritte aus, um allgemeine Informationen zur CLI und zu den unterstützten Befehlen abzurufen: 

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} bei einer Region, einer Organisation und einem Bereich (Space) an. 
    
2. Rufen Sie die Informationen zu den unterstützten Befehlen und zur CLI auf. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud at help 
    ```
    {: codeblock}
    
    

## Hilfe zu einem Befehl abrufen
{: #command_cli_help}

Führen Sie die folgenden Schritte aus, um Hilfeinformationen zur Verwendung eines Befehls abzurufen: 

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} bei einer Region, einer Organisation und einem Bereich (Space) an. 
    
2. Rufen Sie die Liste der unterstützten Befehle ab und identifizieren Sie den gewünschten Befehl. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Rufen Sie die Hilfeinformationen zu dem Befehl ab. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    Dabei ist *Command* der Name eines CLI-Befehls, zum Beispiel *status*. 



## Hilfe zu einem Unterbefehl abrufen
{: #subcommand_cli_help}

Ein Befehl kann Unterbefehle beinhalten. Führen Sie die folgenden Schritte aus, um Hilfeinformationen zu Unterbefehlen abzurufen: 

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} bei einer Region, einer Organisation und einem Bereich (Space) an. 
    
2. Rufen Sie die Liste der unterstützten Befehle ab und identifizieren Sie den gewünschten Befehl. Führen Sie den folgenden Befehl aus:

    ```
    ibmcloud at help 
    ```
    {: codeblock}

3. Rufen Sie die Hilfeinformationen zu dem Befehl ab und ermitteln Sie die unterstützten Unterbefehle. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud at help *Command*
    ```
    {: codeblock}
    
    Dabei ist *Command* der Name eines CLI-Befehls, zum Beispiel *session*. 

4. Rufen Sie die Hilfeinformationen zu dem Befehl ab und ermitteln Sie die unterstützten Unterbefehle. Führen Sie den folgenden Befehl aus: 

    ```
    ibmcloud at *Command* help *Subcommand*
    ```
    {: codeblock}
    
    Dabei gilt Folgendes: 
    
    *Command* ist der Name des CLI-Befehls (zum Beispiel *status*).

    *Subcommand* ist der Name eines unterstützten Unterbefehls. Für den Befehl *session* ist z. B. *list* ein gültiger Unterbefehl. 


## Details des Plug-ins anzeigen
{: #show}
  
Verwenden Sie den Befehl 'ibmcloud plugin show activity-tracker', um Details zu dem Plug-in anzuzeigen.  

```
ibmcloud plugin show activity-tracker
```
{: codeblock}
    




