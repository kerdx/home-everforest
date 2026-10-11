# Everforest per Home Assistant

Tema Home Assistant autonomo ispirato alla palette del tema [Everforest GTK](https://github.com/Fausto-Korpsvart/Everforest-GTK-Theme), con due temi selezionabili separatamente:

- **Everforest Light** — fondo crema, superfici chiare e testo grigio.
- **Everforest Dark** — fondi antracite, superfici grigio-verdi e testo caldo.

La palette è adattata alle variabili colore di Home Assistant: non vengono copiati CSS GTK o lo stile frosted-glass del progetto [homeassistant-frosted-glass-themes](https://github.com/wessamlauf/homeassistant-frosted-glass-themes), citato solo come riferimento per la struttura dei temi HA. Non servono card-mod, UIX o altre dipendenze runtime.

Alcuni colori per testo e selezioni sono scuriti rispetto agli accenti GTK per mantenere un contrasto leggibile sulle superfici di Home Assistant.

## Installazione manuale

1. Copia la directory `themes/` in `config/themes/` nella configurazione di Home Assistant.
2. Se non hai già una sezione `frontend:` in `configuration.yaml`, aggiungi:

   ```yaml
   frontend:
     themes: !include_dir_merge_named themes
   ```

   Se `frontend:` esiste già, aggiungi `themes: !include_dir_merge_named themes` al suo interno senza creare una seconda sezione.
3. Ricarica i temi da **Strumenti per sviluppatori → YAML → Ricarica temi** (la voce può variare in base alla versione) oppure riavvia Home Assistant.
4. Seleziona **Everforest Light** o **Everforest Dark** dal tema del profilo utente.

## Installazione con HACS

Per usare HACS, pubblica prima il progetto in un repository GitHub pubblico. Poi aggiungi l'URL come **repository personalizzato** di categoria **Theme** e installalo. Dopo l'installazione ricarica i temi o riavvia Home Assistant e seleziona la variante desiderata dal profilo. Se la versione di HACS in uso non espone questa categoria o non installa il file del tema, usa l'installazione manuale qui sopra.

## Attribuzione

Everforest è il riferimento cromatico: [Everforest GTK Theme](https://github.com/Fausto-Korpsvart/Everforest-GTK-Theme). Per la convenzione di struttura Home Assistant è stato consultato [homeassistant-frosted-glass-themes](https://github.com/wessamlauf/homeassistant-frosted-glass-themes). Questo progetto è indipendente e non è affiliato ai rispettivi autori.
