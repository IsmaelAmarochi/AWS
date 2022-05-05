<!-- CONTENTS -->
# Inhoud
1. [Introduction](#intro)
2. [Configuration Sets](#config_sets)
    1. [Nieuwe Configuration Set aanmaken](#new_config_set)
    2. [Linken Configuration Set en Cloudwatch](#link_cs_cw)
3. [Identities](#identities)
    1. [Bij het aanmaken van een nieuwe Identity](#new_identity)
4. [Dashboards](#dashboards)
4. [Alarms](#alarms)
5. [SQL Queries](#sql_queries)
6. [FAQ](#faq)

</br>



<!-- INTRODUCTION -->
# Introduction <a id="intro"></a>
Even een klein **documentatie** wat de reporting van AWS SES betreft. Ik zal hier wat meer informatie geven over de werking en het gebruik van deze dashboards.
Om ervoor te zorgen dat men tracking kan uitvoeren op de verschillende metrics van al onze domeinen hebben we hier besloten om gebruik te maken van **Configuration Sets**. 

Momenteel is er maar 1 configuration set aanwezig, namelijk `from_domain`. Een nieuwe configuration set aanmaken kan door de volgende [stappen](#new_config_set) te volgen.

Na het aanmaken van een configuration sets moet men ervoor zorgen dat de metrics naar Cloudwatch worden verstuurd. Cloudwatch gebruikt men om data op te vangen en om er grafieken van te maken. Om de link te leggen tussen de configuration set en Cloudwatch kan men de volgende [stappen](#link_cs_cw) volgen

Eenmaal dat de link is gelegd kan men zich naar Cloudwatch zelf begeven. In Cloudwatch zelf kan men grafieken maken, ik heb 2 manieren gebruikt om data te visualiseren. Het type grafiek dat men gebruikt maakt hier niet uit, hoe men de data gaat ophalen wel. Meer info over de twee manieren van werking vind je [hier](#dashboards).

Een alarm kan opgesteld worden om een admin te verwitiggen via mail wanneer er te veel mails worden verstuurd in een specifieke periode. Hoe men zo een alarm opsteld staat [hier](#alarms) beschreven.

</br>



<!-- CONFIG SETS -->
# Configuration Sets <a id="config_sets"></a>
### **Nieuwe Configuration Set aanmaken <a id="new_config_set"></a>**
Een nieuwe confiuguration set aanmaken kan door de volgende stappen te volgen:
1. **Log in** met een IAM of Root account en begeef je naar de Amazon Simple Email Service.
2. Begeef je naar de Configuration Sets pagina en druk op **Create set**.
3. Geef de Configuration set een passende **naam**.
4. Voor de IP pool kan men voorlopig kiezen voor de **default**.
5. Het is aangeraden om **Transport Layer Security** (*TLS*) te gebruiken om **veiligheid** te garanderen. Druk op het dropdown en vink het vakje aan.
6. Indien men de **Bounce** metrics ook wil gaan tracken kan men **Reputation** metrics aanvinken. Dit kan voor eventuele <u>bijkomende</u> kosten zorgen.

</br>

### **Linken Configuration Set en Cloudwatch  <a id="link_cs_cw"></a>**
Een nieuwe confiuguration set aanmaken kan door de volgende stappen te volgen:
1. **Log in** met een IAM of Root account en begeef je naar de Amazon Simple Email Service.
2. Begeef je op de pagina van de **Configuration Set** die men wil linken.
3. Vervolgens kan men een nieuwe **Event Destination** toevoegen. Dit zorgt ervoor dat de nodige info naar Cloudwatch kan gestuurd worden.
4. Kies welke **metrics** er moeten doorgestuurd worden.
5. Op de volgende pagina moet men **Amazon Cloudwatch aanvinken**.
6. Geef de Cloudwatch destination een passende **naam**.
7. Als laatst moet men een **dimension** toe voegen. In dit geval heb ik de volgende info ingevoerd:
    1. Source: Message `Tag`
    2. Dimension name: `ses:from-domain`
    3. Default value: `0`

</br>

<!-- IDENTITIES -->
# Identities <a id="identities"></a>
### **Bij het aanmaken van een nieuwe Identity <a id="new_identity"></a>**
Als men een nieuwe identity wil gaan toevoegen moet men zeker zijn dat mijn een default **configuration Set** toevoegt. Gebruik hier best de **Configuration Set** die is aangemaakt voor het tracken van de verschillende metrics. 

**Note:** Het domein moet mails <u>versturen</u> om getracked te kunnen worden. Om de configuration te testen kan men een test mail gaan versturen. Bij het versturen van de mail moet men wel een Configuration Set selecteren.

</br>




<!-- DASHBOARDS -->
# Dashboards <a id="dashboards"></a>
Ik heb zelf nu al twee dashboards aangemaakt. Een dashboard bevat verschillende widgets die grafieken kunnen voorstellen. De dashboards die ik heb toegevoegd zijn de volgende: `metrics_per_domain` en `metrics_per_domain_dynamic`.

</br>

### **<u>Manueel</u> - `metrics_per_domain`**
In dit dashboard staan grafieken waar manueel alle domeinen zijn aan toegevoegd. Hoewel dit een goed overzicht geeft van alle domeinen, is het probleem dat men elk nieuw domein hier steeds aan moet toevoegen. Elke grafiek moet dan worden aangepast om het nieuw domein toe te voegen. 

</br>


### **<u>Dynamisch</u> - `metrics_per_domain_dynamic`**

</br>





<!-- ALARMS -->
# Alarms <a id="alarms"></a>

</br>




<!-- SQL QUERIES -->
# SQL Queries <a id="sql_queries"></a>

</br>




<!-- FAQ -->
# FAQ <a id="faq"></a>

</br>
