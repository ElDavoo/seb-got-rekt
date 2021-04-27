Testato su VMWare Workstation, probabilmente va anche su VMWare Player che è gratis.
Nel dubbio, alcuni seriali di VMWare Workstation:

ZF3R0-FHED2-M80TY-8QYGC-NPKYF
YF390-0HF8P-M81RQ-2DXQE-M2UT6
ZF71R-DMX85-08DQY-8YMNC-PPHV8
AZ3E8-DCD8J-0842Z-N6NZE-XPKYF
FC11K-00DE0-0800Z-04Z5E-MC8T6


METODO A (che funziona a tutti tranne che a me, quindi boh):
0) Crea una macchina virtuale in VMWare.
Ricordati di deselezionare UEFI.
Opzioni consigliate se installi Windows 10 LTSC:
RAM: 2GB+
HDD: 15GB
CPU: tutte
1) Apri la cartella dove è creata la macchina virtuale
   (che dovrebbe essere in Documenti > My Virtual Machines)
   e modifica con un editor di testo il file con estensione vmx .
2) Aggiungi SMBIOS.reflectHost = "TRUE" al file.
3) Nelle impostazioni della macchina virtuale, da VMWare, cambia la prima
   metà del MAC Address della scheda di rete virtuale, mettendoci
   la prima metà del MAC address della tua scheda di rete reale.
4) Avvia la macchina virtuale e avviaci VMTest.exe per testare. 
5) Se vuoi e se hai un laptop, per aumentare il "realismo" cerca su VMWare l'opzione
   per inviare le informazioni sulla batteria all'OS Guest, dato che sono dati
   registrati e loggati da SEB.

METODO B (che funziona a tutti ma più lungo):
0) Crea una macchina virtuale in VMWare.
Ricordati di deselezionare UEFI.
Opzioni consigliate se installi Windows 10 LTSC:
RAM: 2GB
HDD: 15GB
CPU: tutte
0b) Puoi installare Windows nel frattempo che fai i passaggi sotto.
1) Avvia VMTest.exe e segnati Manufacturer e Product Name.
2) Installa BiosEdit.exe e apri Phoenix BIOS Editor per modificare il BIOS di VMWare:
2a) Apri BIOS_ORIGINAL.ROM e ignora il warning
2b) Vai sulla scheda DMI Strings
2c) Cambia System Manufacturer Name e System Product name con quelli del tuo PC
2d) File > Build BIOS, salvandolo come BIOS.ROM
Spegni la macchina virtuale se è accesa.
3) Apri la cartella dove è creata la macchina virtuale e modifica
   con un editor di testo il file con estensione vmx .
4) Aggiungi bios440.filename = "BIOS.ROM" al file.
5) Copia il BIOS modificato nella cartella della macchina virtuale
6) Nelle impostazioni della macchina virtuale, da VMWare, cambia la prima
   metà del MAC Address della scheda di rete virtuale, mettendoci
   la prima metà del MAC address della tua scheda di rete reale.
7) Avvia la macchina virtuale e avviaci VMTest.exe per testare. 
8) Se vuoi e se hai un laptop, per aumentare il "realismo" cerca su VMWare l'opzione
   per inviare le informazioni sulla batteria all'OS Guest, dato che sono dati
   registrati e loggati da SEB.

Nota 1: Puoi installare i vmware tools con entrambi i metodi. In caso di dubbio,
	puoi testare velocemente con VMTest.exe .
Nota 2: Puoi applicare la cosa a macchine virtuali già installate.
Nota 3: VMTest.txt spiega la natura dei controlli di SEB.
Nota 4: Nel caso la macchina virtuale non si avvii (schermata nera), prova ad avviare
        con BIOS_ORIGINAL.ROM. Se non va, vuol dire che la versione di VMWare è 
        incompatibile con questo BIOS. Devi quindi estrarre il BIOS da vmware-vmx.exe
        ed applicare la procedura con quel BIOS.
        Un articolo per ispirarti: https://pete.akeo.ie/2011/06/extracting-and-using-modified-vmware.html
