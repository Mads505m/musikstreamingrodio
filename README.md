# Musikstreaming-app i Rust

Velkommen til vores musikstreaming-app, der er udviklet i Rust! Denne app er designet til at være enkel, brugervenlig og robust over for fejl. Den giver brugeren mulighed for at afspille musik, selv når der opstår fejl som:

- Manglende internetforbindelse
- Forkerte brugerinput
- Manglende musikfiler

## Formål

Formålet med dette projekt er at lære at:

- Bygge en musikstreaming-app i Rust ved hjælp af `rodio` til lydafspilning.
- Håndtere fejl og manglende data ved hjælp af `Result` og `Option`.
- Anvende immutability og concurrency ved hjælp af `Arc` og `Mutex`.
- Simulere fejlsituationer som manglende internetforbindelse.
- Strukturere kode i moduler for bedre vedligeholdelse.

## Krav til applikationen

### 1. Visning af Tilgængelige Sange
- Appen skal kunne læse musikfiler (`.mp3`) fra en mappe kaldet `music/`.
- En liste over tilgængelige sange skal vises i terminalen med numre foran, så brugeren nemt kan vælge en sang.
- Hvis der ikke findes nogen musikfiler, skal der vises en fejlmeddelelse.

### 2. Afspilning af Sange
- Brugeren skal kunne vælge en sang ved at indtaste nummeret ud for sangen.
- Sangen afspilles ved hjælp af `rodio` biblioteket.
- Under afspilningen skal brugeren kunne:
  - Pause (`P`)
  - Genoptage (`R`)
  - Stoppe (`Q`)

### 3. Simulering af Streaming
- Appen skal kunne simulere manglende internetforbindelse.
- Brugeren kan afbryde forbindelsen via terminalen.
- Når forbindelsen afbrydes, pauses musikken automatisk.
- Når forbindelsen genoprettes, skal brugeren manuelt kunne genoptage afspilningen.

### 4. Fejlhåndtering
- Brug `Result` og `Option` til at håndtere fejl og manglende data.
- Tilføj passende fejlmeddelelser ved brug af `panic!`, `unwrap()` og `expect()` med forklaringer.
- Brug `?-operatoren` til at forenkle fejlhåndtering.

Appen skal håndtere følgende fejlsituationer:
- Manglende afspilningslister eller musikfiler.
- Ugyldige brugerinput (f.eks. hvis brugeren indtaster tekst i stedet for tal).
- Manglende internetforbindelse under afspilningen.

## Udvidelser og Ekstra Opgaver
Hvis der er ekstra tid, kan applikationen udvides med følgende:

### 1. Opret afspilningslister
- Brugeren skal kunne oprette nye afspilningslister ved at angive et navn.
- Hvis afspilningslisten allerede eksisterer, skal der returneres en fejl.

### 2. Tilføj sange til en afspilningsliste
- Brugeren skal kunne tilføje sange til en eksisterende afspilningsliste.
- Hvis sangen allerede findes på listen, skal der returneres en fejl.

### 3. Brugerautentifikation
- Tilføj en simpel brugeradministration med fejlhåndtering for ugyldige loginforsøg.

## Tips og Tricks

### Installation af `rodio`
Tilføj `rodio` biblioteket til dit projekt:
```sh
cargo add rodio
```
Referencer:
- [Rodio på crates.io](https://crates.io/crates/rodio)
- [Rodio dokumentation](https://docs.rs/rodio/latest/rodio/)

### Import af `rodio`
```rust
use rodio::{Decoder, OutputStream, Sink};
```

### Arbejde med musikfiler
- Brug `read_dir()` fra `std::fs` til at læse filer fra `music/` mappen.
- Brug `Arc<Mutex<>>` til at dele ejerskab og sikre trådsikkerhed ved ændring af internetforbindelsen.
- Brug `?-operatoren` til at propagere fejl op i funktionskald.
- Brug `match` og `if let` til at håndtere `Option` og `Result` værdier.

### Forberedelse af projektet
1. Opret mappen `music/` i projektets rodmappe og tilføj nogle `.mp3` filer.
2. Strukturér koden i moduler:
   - **`main.rs`** → Hovedprogrammet og brugergrænsefladen.
   - **`lib.rs`** → Funktionalitet som:
     - `list_songs()` → Læser musikfiler.
     - `find_song()` → Finder en sangs sti.
     - `play_song()` → Afspiller, pauser og stopper musik.
     - `simulate_internet()` → Simulerer internetforbindelse.

### Fejlhåndtering
- Hvis `music/` mappen ikke findes, skal appen returnere en fejl.
- Hvis brugeren indtaster noget andet end et tal, skal appen returnere en fejl.
- Hvis der ikke findes `.mp3` filer i mappen, skal der returneres en fejl.

---

Dette projekt giver en solid introduktion til Rust-programmering med fokus på fejlhåndtering, lydafspilning og trådsikkerhed. Held og lykke med udviklingen!

