Ziel ist es, Überschussladen eAuto, sowie günstige Tarife von Tibber mit den Möglichkeiten eines Speichers von Senec zu verheiraten.
Mein Problem ist, dass es für mein Auto keine offene Schnittstelle gibt, Senec leider auch eine undokumentierte API nutzt, die lala.cgi heisst und man sich ansonsten mit der Integration vieler verschiedener 
Schnittstellen und Softwareprodukten, wie evcc und solaranzeige oder ioBroker und NodeRed auseinandersetzen muss - was ich definitv nicht wollte!

Insofern sind folgende Dinge zu tun:
1. senec Binding installieren
2. Tibber Binding installieren

Mein aktuelles Projekt kann nun bereits zeitgesteuert optimale Volladungen des Senec Speichers vornehmen, oder auch spontan manuell vorgenommene Volladungen.
Ausstehend ist noch die Wallbox Steuerung, sowie die tatsächliche Prognose Steuerung von Tibber.
Die sehe ich allerdings noch nicht als großes Problem, da das Tibber Binding mit seinen Vorhersagewerten ganz gut funktioniert und die Wallbox Steuerung (ich habe leider eine SENC / ABL)
wahrscheinlich über die gleichen Analysewege zu integrieren ist, wie die manuelle / Zeit /Ereignis gesteuerte Aufladung des Speichers.

Die entsprechenden Kommandos, die man auch über das Senec Frontend zwar geben kann lassen sich leider nicht direkt in Openhab integrieren (zumindest habe ich da keinen anderen Weg gefunden), 
so dass ich per Wireshark & Co. die Post Befehle gesucht - und gefunden habe.

Die findet Ihr in der Datei The Basics.

Die Regeln basieren auf einigen Items, die ich nutze um in meinem Frontend (MainUI und Habpanel) die entsprechenden Einstellungen vorzunehmen.

Die Regeln sind noch recht gesprächig und loggen recht viel, weil ich der ganzen Angelegenheit trotz intensiven Test noch nicht so richtig traue und noch wenigstens einige Wochen beobachten will.

Über die Persistenz Einstellungen fütter ich meinen zentralen InfluxDB und Grafana Service und vergleiche Tibber mit Stromverbrauch und manuelle / forcierte Ladung zu Niedrigtarifzeiten.

welche Logiken würdet Ihr abbilden, um evcc hier überflüssig zu machen und ich gebe mich gerne da dran. Gerne Kommentare und Anregungen posten
Ich bin wirklich neugierig auf Eure Ideen!
