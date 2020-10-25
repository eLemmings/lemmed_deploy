# LemMed
Aplikacja pozwalająca na tworzenie, udostępnianie i przeglądanie **dzienników**, które przechowują wybrany typ i kategorię informacji w czasie. Dziennik może przechowywać jeden z wielu typów danych oraz posiadać wybraną skalę czasu na której będzie uzupełniany.

---
## Cel aplikacji

Aplikacja jest odpowiedzią na wiele problemów związanych ze zdrowiem; Wspomaga ona ocenę i przechowywanie informacji o między innymi:
 * Samopoczuciu (w wybranej skali),
 * Wynikach badań medycznych (np. poziom cukru),
 * Zażywanych lekach i środkach profilaktycznych (dawki antybiotyków, leków przeciwbólowych),
 * Dokonywanych zakupach (np. litry napojów, paczki chipsów),
 * Postępie w walce z nałogiem lub uzależnieniem (wypalone papierosy, wypity alkohol, godziny spędzone na gry komputerowe).

Przez przechowywanie tego typu informacji użytkownik jest w stanie w prosty sposób przejrzeć notowane przez siebie statystyki na wybranej skali i dokonać bardziej adekwatnej samooceny.

Aplikacja może powiadamiać użytkownika i sugerować mu uzupełnienie wybranego dziennika by zapewnić kompletność przechowywanych danych i zachęcić do oceny swojego postępu na bieżąco.

Celem jest zapewnienie użytkownikowi prostego, nieskończenie elastycznego i uniwersalnego sposobu na przechowywanie informacji w przystępnej formie podobnej do arkusza kalkulacyjnego i w efekcie ułatwienie dokonania samooceny swojego ogólnego stanu.

## Projekt i przebieg prac

Projekt aplikacji powstawał w założeniu zapewnienia jak najlepszej merytorycznej podstawy do pełnej implementacji aplikacji.

### Organizacja pracy i podział na grupy

W tym celu drużyna podzielona została wedle zainteresowań i umiejętności na następujące (strategicznie nachodzące na siebie) grupy:
 1. **Projekt**
    * Frontendu
    * Backendu
    * Designu Interfejsu
    * Designu Systemu
 2. **Prototypowanie**
    * Frontendu
    * Backendu
    * Administracji serwerem testowym
 3. **Testy i dokumentacja**
    * Bezpieczeństwa systemu
    * Dokumentacji

### Ogólne ustalenia i harmonogram

Przez współpracę wszystkich członków zespołu ustalono przydział do poszczególnych grup, sformułowany został główny problem a następnie, po wielu godzinach dyskusji, utworzony został wstępny i bardzo ogólny projekt jego rozwiązania. Po wstępnych ustaleniach powstał harmonogram, którym ustalono w jaki sposób przebiega praca poszczególnych grup z uwzględniem równoległej pracy i ewentualnych zapasów czasowych w przypadku trudności.

Poglądowy harmonogram został zaprezentowany poniżej.

***Harmonogram goes here..***

### Projekt i wykonanie

Zgodnie z harmonogramem przez następne dni powstawały:
 * Diagram przypadków użycia,
 * Projekt architektury z podziałem na frontend i backend,
 * Wizje wyglądu aplikacji,
 * Pomysły na rozszerzenie funkcjonalności aplikacji.

Wszystkie ważniejsze dokumenty znajdują się poniżej:

***Dokumenty go here***

Po w miarę dokładnym ustaleniu ostatecznej formy aplikacji nastąpiła faza implementacji prototypu, który obrazowałby główne założenia projektu.

\ Detale co do projektowania frontendu
\ Detale co do projektowania backendu

### Konfiguracja prototypowego serwera
\ Detale co do konfiguracji serwera
\ Detale co do wdrażania tego czegoś
\ ...

### Podsumowanie
\ Podsumowanie

## Detale implementacji prototypu

Aplikacja została zaimplementowana w modelu klient-serwer przy wykorzystaniu następującego stosu technologicznego:

### Backend aplikacji
Implementacja warstwy serwera przechowującego opiera się głównie przy wykorzystaniu języka skryptowego **Python** w wersji **3.9**. Pozwala to na dużą rozszerzalność i swobodę implementacji, umożliwiając dodatkowo niemal natychmiastowe wprowadzanie wszelkich zmian i poprawek po stronie serwera.

Modułem umożliwiającym utworzenie serwera aplikacji w języku Python jest `Flask`. Ze względu na prostą architekturę aplikacji, jest to optymalny wybór który pozwala na bezproblemową implementację i duży potencjał rozwoju.

Połączenie z bazą danych rozwiązane jest przy użyciu modułu `SQLAlchemy`, który pozwala na proste zarządzanie zawartością i pozyskiwanie informacji z bazy danych.

Do przechowywania danych wybrano relacyjną bazę danych opartą na bibliotece `SQLite` w wersji 3. Jest ona wysoce wydajna i bez zbędnych mechanizmów zapewnianych już przez wyższe warstwy aplikacji.

**Technologie:** (podstawa - `Python 3.9`)
 * Serwer - `Flask`,
 * Baza danych - `SQLite3`,
 * Interfejs bazy danych - `SQLAlchemy`.

\ Dokumentacja (coś w tym stylu przynajmniej) goes here

### Frontend aplikacji
Implementacja warstwy użytkownika opiera się na (...) [niech idiota od frontendu się tłumaczy ze swoich grzechów]

**Technolgie:** (podstawa - `React`, `JavaScript`)
 * Przekierowania i logowanie - `React Router`
 * Manipulacja treścią - `ReactDOM`
 * Interfejs Użytkownika - `Material-UI`

\ Dokumentacja (coś w tym stylu przynajmniej) goes here
