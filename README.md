WBEN
====

Fast deployable Wireless Baloon Emergency Network


Il progetto PiBaloon (ora Wireless Baloon Emergency Network)  nasce dopo l'emergenza del terremoto in Emilia del 2012, dove è stato possibile osservare le fragilità dell’infrastruttura GSM che utilizzano i cellulari per i servizi di chiamata e invio di SMS. Prendendo in considerazione la percentuale di dispositivi elettronici in grado di accedere a reti WiFi 802.11 come smartphone, tablet, netbook, ecc… che ormai la maggiorparte delle persone possiede è ragionevole pensare che un sistema “a celle” che comunichi sugli standard 802.11 con servizi leggeri e a rapido dispiego sia una soluzione possibile alle situazioni di emergenza in aiuto ai sistemi tutt’ora operativi come i ponti radioamatoriali e le sale radio dislocate nei centri di protezione civile.


Lo scopo del progetto è quindi quello di creare una rete wireless autonoma di emergenza che renda i dispositivi elettronici mobili, utilizzabili per recuperare informazioni utili in condizioni di emergenza.
Oltre all’esperienza del terremoto anche quella maturata nel progetto Ninux ha influito allo sviluppo del progetto in particolare la topologia a mesh e gli algoritmi di routing ad alta riconfigurabilità e resilienza implementati in un firmware (Libre Mesh) utilizzato dal gruppo di Bologna e non solo, si prestano eccezionalmente allo scopo del progetto.


Il nodo WBEN è composto da un pallone pieno di gas elio che si innalza a 20/30mt di altezza portando con se un accesspoint wireless composto da due antenne, una omnidirezionale che espone una rete protetta con cui i palloni formano una rete mesh tra di loro e un'antenna a pannello con irradiazione verso terra che dà accesso agli utilizzatori del servizio di emergenza.


Collegandosi alla rete e cercando di navigare su una pagina web qualunque,  si verra' rediretti ad un server localizzato a terra rispetto al nodo (e collegato ad esso tramite ethernet) che espone la pagina principale con l'elenco dei servizi offerti dalla rete, dello stato dei soccorsi e della situazione generale attraverso una bacheca publica in cui i vari enti registrati (Protezione Civile, VF, CC…) possono scrivere liberamente.


L'idea è quella di non offrire internet direttamente agli utilizzatori della rete di emergenza, ma solamente di implementare per ora due servizi basilari (posta e VoIP) per comunicazioni interne. 


HARDWARE:
Al momento il prototipo è stato costruito con una scatola stagna di pvc con dentro la scheda di un Tp-Link WR-841ND (la version senza antenne staccabili è la "WR-841N").
Si tratta appunto di una versione prototipale utile ad eseguire i primi test ma sopratutto per contenere i costi visto che ad oggi il progetto è compleamente autofinanziato.
Sono state pensate molte implementazioni diverse a livello hardware del progetto in un breve elenco che poi verrà affrontato meglio nella parte “futuri sviluppi”:

-accessori per il pallone:         
tele in kevlar per aumentarne la resistenza, spoiler per aumetare la stabilità e la resistenza al vento

-custodie in polistirolo rivestite per l’elettronica di bordo

-antenne autocostruite (abbiamo l’attrezzatura completa per farle!) per migliorare le prestazioni a discapito del peso

-router board dedicate come la alix3d2 che ha appunto due slot miniPCI in cui alloggiare due radio differenti


FIRMWARE:
Il firmware utilizzato è libre-mesh, è stato scelto perchè è progettato per construire reti mesh e perchè è divenuto lo standard utilizzato dal Ninux di Bologna e dopo una breve analisi ci è sembrato ottimo anche per questo progetto.


SOFTWARE:
Per fornire i servizi sopra annunciati, si pensa di utilizzare un server zeroshell configurato come captive portal la cui splash page visualizza le seguenti informazioni:
*  Stato dei soccorsi
* Informazioni utili su come/dove trovare assistenza
* Informazioni utili per mantenere la calma (es: che i cellulari non possono effettuare finchè il servizio non viene ripristinato)
*  Elenco dei servizi offerti dalla WBEN
* Autenticazione per accedere ai servizi


Per l’autenticazione degli utenti l’idea è quella di utilizzare i servizi forniti da RADIUS principalmente per la semplicità nel classificare gli utenti in domini differenti (spero di capire come si configura per farlo distribuito!!!)


 Utenti locali al WBEN:
    - registrazione di un utente propagato su tutti i server
    - informazioni base dell'utente utili ad essere contattati
 Servizio di posta:
    - gestito tramite gli utenti locali della WBEN
    -
