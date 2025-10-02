# Prova finale di algoritmi e strutture dati A.A. 2023-2024
Politecnico di Milano – Corso di Algoritmi e Principi dell’Informatica  
Docente: Alessandro Barenghi

## Introduzione
Il presente progetto costituisce la **prova finale del corso di Algoritmi e Strutture Dati (a.a. 2023/2024)** e ha come obiettivo l’implementazione, in linguaggio **C (standard C11)**, di un simulatore per la gestione di una pasticceria industriale.  
Il lavoro si focalizza su:
- applicazione pratica delle tecniche studiate durante il corso;  
- attenzione agli aspetti di **efficienza in tempo e memoria**;  
- adozione di strutture dati adeguate per la risoluzione del problema.  

## Specifiche del problema
La simulazione è modellata a **tempo discreto** (con istante iniziale pari a 0) e deve gestire i seguenti elementi:  
- **Ricette**: ciascuna ricetta è identificata da un nome e da un insieme di ingredienti con quantità associate.  
- **Magazzino**: contiene i lotti di ingredienti, caratterizzati da quantità e data di scadenza.  
- **Ordini**: richieste di clienti relative a uno o più dolci. Gli ordini vengono evasi se vi sono ingredienti sufficienti, altrimenti sono posti in attesa.  
- **Corriere**: passa periodicamente a ritirare gli ordini evasi, soggetto a una capienza massima del furgone. Gli ordini vengono caricati rispettando criteri di peso e ordine cronologico.  

Ogni comando ricevuto dall’ingresso standard rappresenta un avanzamento temporale di un’unità.  

## Comandi previsti
Il sistema riceve comandi da **stdin** e produce risposte su **stdout**.  
I comandi supportati sono:

- `aggiungi_ricetta <nome_ricetta> <nome_ingrediente> <quantità> ...`  
  ➝ Inserisce una nuova ricetta nel catalogo.  
  Output: `aggiunta` oppure `ignorato`.

- `rimuovi_ricetta <nome_ricetta>`  
  ➝ Elimina una ricetta, se non associata ad ordini pendenti.  
  Output: `rimossa`, `ordini in sospeso`, `non presente`.

- `rifornimento <nome_ingrediente> <quantità> <scadenza> ...`  
  ➝ Aggiorna il magazzino con nuovi lotti.  
  Output: `rifornito`.

- `ordine <nome_ricetta> <numero_elementi>`  
  ➝ Registra un nuovo ordine.  
  Output: `accettato` oppure `rifiutato`.

In corrispondenza dell’arrivo del corriere (tempo multiplo della periodicità fissata), il programma stampa il contenuto del furgone oppure, se vuoto, il messaggio `camioncino vuoto`.

## Esempio di funzionamento
Presente con commenti nel file "specifiche progetto api".

## Dettagli implementativi
- **Linguaggio**: C (C11), senza utilizzo di librerie esterne oltre la libreria standard.  
- **Modello di esecuzione**: input da `stdin`, output su `stdout`.  
- **Vincoli**: nessun multithreading, nessuna gestione concorrente.  

## Modalità di compilazione ed esecuzione
Compilare con:  
gcc -std=c11 -Wall -Wextra -O2 -o pasticceria main.c  

Eseguire con:  
./pasticceria < input.txt > output.txt
