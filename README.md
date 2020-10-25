# LemMed

Aplikacja pozwalająca na tworzenie, udostępnianie i przeglądanie **dzienników**, które przechowują wybrany typ i kategorię informacji w czasie. Dziennik może przechowywać jeden z wielu typów danych oraz posiadać wybraną skalę czasu na której będzie uzupełniany.

---

## Cel aplikacji

Aplikacja jest odpowiedzią na wiele problemów związanych ze zdrowiem; Wspomaga ona ocenę i przechowywanie informacji o między innymi:

- Samopoczuciu (w wybranej skali),
- Wynikach badań medycznych (np. poziom cukru),
- Zażywanych lekach i środkach profilaktycznych (dawki antybiotyków, leków przeciwbólowych),
- Dokonywanych zakupach (np. litry napojów, paczki chipsów),
- Postępie w walce z nałogiem lub uzależnieniem (wypalone papierosy, wypity alkohol, godziny spędzone na gry komputerowe).

Przez przechowywanie tego typu informacji użytkownik jest w stanie w prosty sposób przejrzeć notowane przez siebie statystyki na wybranej skali i dokonać bardziej adekwatnej samooceny.

Aplikacja może powiadamiać użytkownika i sugerować mu uzupełnienie wybranego dziennika by zapewnić kompletność przechowywanych danych i zachęcić do oceny swojego postępu na bieżąco.

Celem jest zapewnienie użytkownikowi prostego, nieskończenie elastycznego i uniwersalnego sposobu na przechowywanie informacji w przystępnej formie podobnej do arkusza kalkulacyjnego i w efekcie ułatwienie dokonania samooceny swojego ogólnego stanu.

## Projekt i przebieg prac

Projekt aplikacji powstawał w założeniu zapewnienia jak najlepszej merytorycznej podstawy do pełnej implementacji aplikacji.

### Organizacja pracy i podział na grupy

W tym celu drużyna podzielona została wedle zainteresowań i umiejętności na następujące (strategicznie nachodzące na siebie) grupy:

1.  **Projekt**
    - Frontendu
    - Backendu
    - Designu Interfejsu
    - Designu Systemu
2.  **Prototypowanie**
    - Frontendu
    - Backendu
    - Administracji serwerem testowym
3.  **Testy i dokumentacja**
    - Bezpieczeństwa systemu
    - Dokumentacji

### Ogólne ustalenia i harmonogram

Przez współpracę wszystkich członków zespołu ustalono przydział do poszczególnych grup, sformułowany został główny problem a następnie, po wielu godzinach dyskusji, utworzony został wstępny i bardzo ogólny projekt jego rozwiązania. Po wstępnych ustaleniach powstał harmonogram, którym ustalono w jaki sposób przebiega praca poszczególnych grup z uwzględniem równoległej pracy i ewentualnych zapasów czasowych w przypadku trudności.

Poglądowy harmonogram został zaprezentowany poniżej.

![Harmonogram](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image4.PNG)

### Projekt i wykonanie

Zgodnie z harmonogramem przez następne dni powstawały:

- Diagram przypadków użycia,
  ![Diagram przypadków użycia](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image5.PNG)
- Projekt architektury z podziałem na frontend i backend,
  - backend
    ![Architektura backendu](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image6.PNG)
  - frontend
    ![Architektura frontendu](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image7.PNG)
- Wizje wyglądu aplikacji,
  ![Wizja działania aplikacji](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image8.PNG)
- Pomysły na rozszerzenie funkcjonalności aplikacji.
  ![Pomysły funkcjonalności](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image9.PNG)
- W widoku tych kafelków można doszukiwać się pewnych `wzorów`. Widać kiedy coś szło dobrze a kiedy gorzej. Ułatwia to analizę samego siebie.
  ![Widok wpisów](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image10.PNG)

  ### Konfiguracja prototypowego serwera
W celu zapewnienia szybkiej i prostej możliwości wdrożenia prototypu w dowolnym środowisku zastosowaliśmy konteneryzacje zrealizowaną za pomocą oprogramowania **docker**. Dzięki temu rozwiązaniu wdrożenie naszego prototypu, np. na serwerze VPS, jest bardzo łatwe i sprowadza się do wykonania kilku poleceń.

**Kontenery**
 * front - Serwer aplikacji klienckiej. Działa na porcie 80 poprzez nginx
 * back - Serwer udostępniający API. Działa na porcie 5000 poprzez uwsgi
 * nginx - Serwer główny działający jako reverse proxy. Pozwala on na działanie zarówno aplikacji klienkiej jak i API pod jednym publicznym adresem IP.

**Instrukcja wdrożenia aplikacji**
1. Upewnij się że na serwerze zainstalowane są narzędzia: [git](https://git-scm.com/), [docker](https://www.docker.com/) oraz [docker-compose](https://docs.docker.com/compose/install/). W systemie Ubuntu Linux sprowadza się to do wykonania następujących poleceń:
```bash
sudo apt-get install git docker docker-compose
```
2. Pobierz kod aplikacji z [repozytorium github](https://github.com/eLemmings/lemmed_deploy) i przejdź do głównego katalogu repozytorium.
```bash
git clone --recurse-submodules https://github.com/eLemmings/lemmed_deploy

cd lemmed_deploy
```
3. Zbuduj kontenery
```bash
docker-compose build
```
4. Uruchom kontenery
```bash
docker-compose up
```

## Detale implementacji prototypu

Aplikacja została zaimplementowana w modelu klient-serwer przy wykorzystaniu następującego stosu technologicznego:

### Backend aplikacji

Implementacja warstwy serwera przechowującego opiera się głównie przy wykorzystaniu języka skryptowego **Python** w wersji **3.9**. Pozwala to na dużą rozszerzalność i swobodę implementacji, umożliwiając dodatkowo niemal natychmiastowe wprowadzanie wszelkich zmian i poprawek po stronie serwera.

Modułem umożliwiającym utworzenie serwera aplikacji w języku Python jest `Flask`. Ze względu na prostą architekturę aplikacji, jest to optymalny wybór który pozwala na bezproblemową implementację i duży potencjał rozwoju.

Połączenie z bazą danych rozwiązane jest przy użyciu modułu `SQLAlchemy`, który pozwala na proste zarządzanie zawartością i pozyskiwanie informacji z bazy danych.

Do przechowywania danych wybrano relacyjną bazę danych opartą na bibliotece `SQLite` w wersji 3. Jest ona wysoce wydajna i bez zbędnych mechanizmów zapewnianych już przez wyższe warstwy aplikacji.

**Technologie:** (podstawa - `Python 3.9`)

- Serwer - `Flask`,
- Baza danych - `SQLite3`,
- Interfejs bazy danych - `SQLAlchemy`.

**Dokumentacja do API:** https://github.com/eLemmings/back/blob/ba5dbc5f64625b61150ce53f12a9393fba060f02/docs/api.md

### Frontend aplikacji

Implementacja warstwy użytkownika opiera się głównie przy wykorzystaniu języka skryptowego **Javascript**. Język ten wykorzystywany jest przez przeglądarki, które różnie implementują funkcję dostępne w tym języku. Niektóre z nich nie są dostępne wszędzie.

Z wyżej wymienionych powodów wybrano `Reacta`. Jest on powszechny i łatwo się go implementuje. Można w nim prosto zarządzać komponentami, dzięki czemu można myśleć o dalszym rozwoju. Oprócz tego napisany kod trafia do transkompilatora. W nim zostaje przekształcona składnia, która nie jest zaimplementowana we wszystkich przeglądarkach.

Do budowania interfejsu użytkownika wybrano Material-UI. Jest to dedykowane narzędzie do budowania komponentów w React. Przyśpiesza pracę i pozwala w prosty sposób stworzyć wygląd interfejsu, która wygląda profesjonalnie.

**Technologie:** (podstawa - `React`, `JavaScript`)

- Przekierowania i logowanie - `React Router`
- Komponenty bezstanowe i stanowe - `React hooks, React state`
- Manipulacja treścią - `ReactDOM`
- Interfejs Użytkownika - `Material-UI`
- Moduły plików scss - `Css Modules`

### Interfejs aplikacji

Prototyp aplikacji w swojej ostatecznej formie wygląda bardzo podobnie do wykonanych makiet.
![Pomysły funkcjonalności](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image1.PNG)

1. Przejście do poporzedniego dziennika
2. Przejście do następnego dziennika
3. Wybór konkretnego dziennika z listy
4. Dodanie wpisu do dziennika
5. Skala dotycząca ilości pojawianych się wpisów
6. Edycja, podgląd wpisu
7. Menu z opcjami użytkownika i dziennika

Dodawanie dzienników opiera się na formularzu zamiesczonym poniżej.

![Pomysły funkcjonalności](https://github.com/eLemmings/lemmed_deploy/blob/master/images/image1.PNG)

1. Pole z nazwą dziennika
2. Suwak ze skalą wartości przechowywanych w dzienniku. Wartość domyślna `2`, działa jak typ **boolean**. Można mieć tylko dwa stany. Im mniejsza wartość tym niższa przeźroczystość.
3. Kolor dziennika, na bazie którego będa dodawane wpisy.
