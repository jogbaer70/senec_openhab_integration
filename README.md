Ziel ist es, Überschussladen eAuto, sowie günstige Tarife von Tibber mit den Möglichkeiten eines Speichers von Senec zu verheiraten.
Mein Problem ist, dass es für mein Auto keine offene Schnittstelle gibt, Senec leider auch eine undokumentierte API nutzt, die lala.cgi heisst und man sich ansonsten mit der Integration vieler verschiedener 
Schnittstellen und Softwareprodukten, wie evcc und solaranzeige oder ioBroker und NodeRed auseinandersetzen muss - was ich definitv nicht wollte!

Insofern sind folgende Dinge zu tun:
1. senec Binding installieren
2. Tibber Binding installieren (brauchen wir jetzt noch nicht, wird aber in Kürze kommen)

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


English version
The goal is to combine excess solar charging for an EV with Tibber’s dynamic electricity tariffs while leveraging a Senec battery storage system.

My main challenge is that my EV lacks an open interface, and Senec uses an undocumented API called lala.cgi. Without direct support, you’d typically need to integrate multiple systems like EVCC, Solaranzeige, ioBroker, and Node-RED—something I definitely did not want to deal with!

To achieve this, the following steps are required:
	•	Install the Senec binding
	•	Install the Tibber binding (not needed yet, but will be soon)

At this stage, my setup can already optimize full battery charges in the Senec storage unit either on a scheduled basis or through manual overrides. What’s still missing is Wallbox control and forecast-based automation using Tibber. However, I don’t see this as a major issue, since the Tibber binding provides solid predictions, and I expect that my Senec/ABL Wallbox can be integrated using the same reverse engineering approach I applied to manual/time/event-based battery charging.

The relevant commands are accessible via the Senec frontend, but they can’t be integrated into OpenHAB directly (at least, I haven’t found a way). To work around this, I used Wireshark & Co. to analyze and extract the necessary POST requests.

You can find these commands in the file “The Basics.”

How the rules work:

The rules rely on several OpenHAB items that I use to configure settings in my MainUI and HABPanel interfaces.

Right now, the rules are very verbose and log quite a bit. Despite extensive testing, I still don’t fully trust the system, so I plan to monitor everything for a few more weeks before considering it stable.

Data Logging & Comparison

Through persistence settings, I feed data into my central InfluxDB and Grafana instance, comparing Tibber price forecasts, electricity consumption, and forced/manual low-tariff charging.

Looking for Ideas!

What logic would you implement to make EVCC unnecessary in this setup? I’d love to hear your comments and suggestions—I’m genuinely curious about your ideas! 🚀