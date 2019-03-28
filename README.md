# Vårdområden
Vårdområden för äldreomsorgen i Sjöbo kommun

Under hösten 2017 inleddes dialog med Vård- och omsorgsförvaltningen. Förvaltningen ser positivt på GIS-tillämpning, vad gäller till exempel dynamisk kartläggning av kunder samt ruttplanering. Det första steget är emellertid att kartlägga de s.k. vårdområden som används inom förvaltningen. Under hösten 2017 har Daniel Lundqvist skickat in Excel-listor med information om gata och vilket vårdområde den tillhör. Excel-filen heter Vardomraden och ligger i mappen G:\SB GIS projekt\Vårdområden. Där finns även skisser över vårdområdena som Daniel har skickat in. Baserat på Excel-filen, filen reAdress i sde_geofir (FastighetsModell), samt filen fastighetsytor_1265 i sde_gsd har ett FME-skripts tagits fram för att skapa vårdområdena. Skriptet är dokumenterat och finns i mappen G:\SB GIS\Arbetsytor FME\IP_Vårdområden. Leverans skedde 2018-03-23 med en Leaflet-lösning, denna lösning finns beskriven i koden.  

Framtagning av vårdområden: Utgick från en FME-snurra mot fastigheter (läsa ut adress från fastighet och lägga fastighetsytan med adressen i rätt vårdområde), men den klarade dels inte att fånga alla fastighetsytor och inte heller de delar där tex huset ligger på ena sidan vägen på fastigheten och resten av fastigheten ligger på andra sidan vägen, och där vägen skall vara områdesgräns. Utgick då från resultatet från FME, och sedan justerade polygoner ”för hand” (klippte de delar som gick att klippa med fastighetslagret utifrån vårdområdestillhörighet) i QGIS, som följer gränserna från FME-scriptet, i samråd med de som ville ha kartan så att alla adresser hamnar i rätt vårdområde. En ganska osmidig approach, men lyckades inte lura ut ett smidigare/automatiserat sätt. 

Presentationslösning: Leaflet är javascript, med några egna funktioner som gör det lämpligt för karttjänster på webben. Data som hör till kan antligen läggas som tjänster av typen WMS, eller packeterade som .json-filer (omdöpta till .js). Det som är viktigt att tänka på är att i det senare fallet ligger data helt öppet för hemsidebesökaren om denna läggs i samma mapp som hemsidan (det vill säga, besökaren kan ladda ner data-setet utan att vi har kontroll på vem som laddar ner vad och hur många gånger). Denna lösning är alltså inte användbar för data som av olika anledningar är av känslig/sekretessbelagd natur. Själva Leaflet-filen (karta_sjobo.html) finns i katalogen SB GIS Projekt/VårdområdenLeaflet. 
