# Raport z testów manualnych aplikacji OrangeHRM Demo  
Przygotowany zgodnie z dobrymi praktykami i terminologią ISTQB

### 1. Wprowadzenie

Celem raportu jest przedstawienie wyników testów manualnych wybranych funkcjonalności aplikacji OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/), przeprowadzonych w środowisku testowym na koncie Admin. Dokument został opracowany zgodnie z zaleceniami ISTQB, z zachowaniem właściwej terminologii, struktury oraz kompletności informacji testerskich.

### 2. Zakres testów (Test Scope)

**Moduły objęte testami:**
- Zarządzanie pracownikami (PIM – Personal Information Management)
- Zarządzanie strukturą organizacyjną (Organization Structure)
- Logowanie (Login)
- Interfejs użytkownika (UI/UX)

**Zakres funkcjonalny:**  
Podstawowe scenariusze CRUD, zarządzanie strukturą firmy (przeglądanie, dodawanie, edycja i usuwanie jednostek organizacyjnych), testy użyteczności formularza logowania oraz ergonomii interfejsu.

**Zakres nieobjęty testami:**  
Integracje zewnętrzne, raportowanie, uprawnienia innych ról użytkowników.

### 3. Środowisko testowe (Test Environment)

- Przeglądarki: Google Chrome (v138), Mozilla Firefox (v127+)
- Tryb mobilny: Chrome DevTools – tryb responsywny
- System operacyjny: Windows 10
- Urządzenie mobilne: Mi Note 10 Lite, Google Chrome (v138), Android 12
- Dane testowe: generowane na potrzeby testów, niepochodzące z produkcji
- Wersja aplikacji: aktualna wersja demo na dzień testów (11.07.2025)

### 4. Wykorzystane narzędzia

- Google Chrome, Mozilla Firefox
- Chrome DevTools (inspekcja, analiza sieci)
- Mi Note 10 Lite (Android 12)
- Markdown (dokumentacja)
- GitHub (kontrola wersji dokumentacji)
- Zrzuty ekranu i nagrania wideo (załączniki)

### 5. Ograniczenia testów (Test Constraints)

- Testy przeprowadzono wyłącznie na koncie Administratora – brak możliwości weryfikacji procesów dostępnych dla innych ról użytkowników (np. pracownika).
- Brak dostępu do dokumentacji wymagań biznesowych (traceability na podstawie eksploracji).
- Ograniczony czas na wykonanie testów.

### 6. Przypadki testowe (Test Cases) i pokrycie wymagań

| ID TC      | Warunek testowy                                      | Kroki testowe                                                                                                  | Dane testowe                    | Oczekiwany rezultat                                                    | Status    | Komentarz                                                          |
|------------|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|----------------------------------|------------------------------------------------------------------------|-----------|---------------------------------------------------------------------|
| TC-PIM-01  | Dodanie nowego pracownika                            | 1. PIM → Add Employee 2. Wprowadź dane 3. Zapisz                                                              | Imię: Jan, Nazwisko: Testowy, ID: 12345 | Pracownik widoczny na liście                          | Sukces    | Można pominąć dodanie awatara – system przypisuje domyślny obrazek  |
| TC-PIM-02  | Wyszukiwanie pracownika                              | 1. Employee List 2. Wyszukaj po imieniu/nazwisku                                                               | Imię: Jan, Nazwisko: Testowy     | Pracownik wyświetlony na liście                       | Sukces    |                                                                     |
| TC-PIM-03  | Edycja danych pracownika                             | 1. Wybierz pracownika 2. Edytuj dane 3. Zapisz                                                                 | Zmiana nazwiska na: Testerski    | Dane zaktualizowane                                   | Sukces    |                                                                     |
| TC-PIM-04  | Usunięcie pracownika                                 | 1. Przejdź do PIM → Employee List 2. Wyszukaj pracownika (np. Jan Testerski) 3. Zaznacz...                     | Pracownik: Jan Testerski         | Pracownik usunięty z listy                            | Sukces    |                                                                     |
| TC-PIM-05  | Walidacja uploadu zdjęcia – rozmiar/typ pliku        | 1. PIM → Add Employee 2. Wprowadź dane 3. Wybierz plik testowy.png (>1 MB) lub zły typ 4. ...                  | testowy.png (>1 MB) lub plik niebędący obrazem | Komunikaty walidacyjne, brak możliwości zapisu         | Sukces    | Walidacja działa już na etapie wyboru pliku – komunikaty są czytelne i precyzyjne |
| TC-ORG-00  | Przeglądanie struktury organizacyjnej                | 1. Admin → Organization → Structure 2. Sprawdź, czy wyświetlają się jednostki                                  | —                                | Lista jednostek widoczna w strukturze                  | Sukces    | Struktura organizacyjna wyświetla się poprawnie po wejściu w moduł  |
| TC-ORG-01  | Dodanie jednostki organizacyjnej                     | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Dodaj nową jednostkę 4. Wprowadź...                   | Nazwa: Testowa Jednostka         | Jednostka widoczna w strukturze                       | Sukces    | Dodanie możliwe po wcześniejszym kliknięciu „Edit”                  |
| TC-ORG-02  | Edycja jednostki organizacyjnej                      | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Wybierz jednostkę 4. Edytuj...                        | Zmiana nazwy: z „Testowa Jednostka” na „Zmieniona Jednostka” | Zaktualizowana nazwa w strukturze           | Nieudany  | Komunikat „Error: Invalid Parameter” po próbie zapisania – zmiana nie jest możliwa. |
| TC-ORG-03  | Usunięcie jednostki organizacyjnej                   | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Wybierz jednostkę 4. Usuń 5. ...                      | Jednostka: Testowa Jednostka     | Jednostka usunięta ze struktury                       | Sukces    | Usunięcie możliwe bezpośrednio po utworzeniu jednostki, niezależnie od błędu edycji |
| TC-LOGIN-01| Brak możliwości podejrzenia hasła                    | 1. Otwórz ekran logowania na urządzeniu mobilnym 2. Wpisz hasło w pole Password 3. Sprawdź, czy dostępna jest opcja „pokaż/ukryj hasło” (np. ikona oka) | Hasło: admin123                  | Użytkownik może podejrzeć wpisywane hasło              | Nieudany  | Brak opcji podglądu hasła. Pole hasła zawsze zamaskowane.           |
| TC-UI-01   | Ocena czytelności rozmieszczenia przycisków          | 1. Zaloguj się jako Admin 2. Przeglądaj różne moduły 3. Zwróć uwagę na rozmieszczenie przycisków akcji 4. Udokumentuj obserwacje nagraniem ekranu | —                                | Przejrzyste i logiczne rozmieszczenie przycisków akcji | Nieudany  | Przyciski są rozmieszczone w sposób nieintuicyjny. Dotyczy m.in. PIM i Organization Structure. |
| TC-UI-02   | Zwijanie przycisku/menu                              | 1. Otwórz aplikację 2. Kliknij przycisk/menu, który powinien się zwijać                                        | —                                | Przycisk/menu zwija się po kliknięciu lub zmianie stanu| Nieudany  | Przycisk się nie zwija.                                            |
| TC-UI-03   | Sprawdzenie dostosowania wideo do rozmiaru ekranu    | 1. Otwórz aplikację na urządzeniu mobilnym 2. Przejdź do ekranu z wideo 3. Obserwuj, czy wideo dostosowuje się do rozmiaru ekranu | Brak specyficznych danych testowych | Wideo powinno automatycznie dostosowywać się do rozmiaru ekranu | Nieudany  | Wideo nie dostosowuje się do zmiany rozmiaru ekranu                |
| TC-UI-04   | Sprawdzenie poprawnego wyświetlania strony           | 1. Otwórz aplikację na urządzeniu mobilnym 2. Przeglądaj różne podstrony i sekcje 3. Obserwuj, czy elementy strony nie nachodzą na siebie i są poprawnie rozmieszczone | Brak specyficznych danych testowych | Wszystkie elementy strony są poprawnie rozmieszczone i nie nachodzą na siebie | Nieudany  | Strona rozjeżdża się, elementy nachodzą na siebie            |

### 7. Dane testowe (Test Data)

- Pracownik: Imię: Jan, Nazwisko: Testowy, ID: 12345
- Modyfikacja: Zmiana nazwiska na „Testerski”
- Jednostka organizacyjna: Nazwa: Testowa Jednostka, Nowa nazwa: Zmieniona Jednostka
- Logowanie: Użytkownik: Admin, Hasło: admin123

### 8. Log testowy (Test Log)

| Data        | Tester         | Moduł         | TC           | Wynik   | Komentarz                                                        |
|-------------|---------------|---------------|--------------|---------|------------------------------------------------------------------|
| 2025-07-10  | Kasper Żdaniec| PIM           | Wszystkie    | OK      | Wszystkie przypadki PIM zakończone sukcesem                      |
| 2025-07-11  | Kasper Żdaniec| Organization  | Wszystkie    | OK/Fail | Dodanie i usunięcie jednostki OK, edycja zakończona błędem       |
| 2025-07-11  | Kasper Żdaniec| Login         | TC-LOGIN-01  | Fail    | Brak możliwości podejrzenia hasła                                |
| 2025-07-11  | Kasper Żdaniec| UI/UX         | TC-UI-01, 02, 03, 04 | Fail    | Przyciski akcji rozmieszczone nieintuicyjnie; brak zwijania menu; wideo nie dostosowuje się do ekranu; strona rozjeżdża się |

### 9. Wyniki testów, defekty i usprawnienia (Defects & Improvements)

| ID     | Opis                                                                 | Moduł            | Priorytet | Kroki                                                                                                                    | Oczekiwany rezultat                                                    | Rzeczywisty rezultat                                                      | Środowisko                                                      | Załącznik   |
|--------|---------------------------------------------------------------------|------------------|-----------|--------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|----------------------------------------------------------------------------|------------------------------------------------------------------|-------------|
| DEF-01 | Zmiany po edycji pracownika nie są widoczne bez przeładowania        | PIM              | Średni    | 1. Zaloguj się jako Admin 2. Przejdź do PIM 3. Edytuj dane pracownika 4. Zapisz zmiany 5. Obserwuj dane na liście pracowników | Dane pracownika powinny być natychmiast widoczne po zapisaniu.         | Zmiany widoczne dopiero po ręcznym przeładowaniu strony (F5 lub Refresh). | Chrome 138, Firefox 127, Windows 10, demo 2025-07-11            | [DEF-01.png](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/09a3e5302a35e9e277ea0dc97bf2c90ccdae69a4/attachments/DEF-01.png)  |
| DEF-03 | Błąd „Error: Invalid Parameter” przy edycji jednostki organizacyjnej | Organization     | Wysoki    | 1. Zaloguj się jako Admin 2. Przejdź do Admin → Organization → Structure 3. Kliknij „Edit” 4. Wybierz jednostkę 5. Zmień nazwę 6. Zapisz | Nazwa jednostki powinna zostać zaktualizowana i widoczna w strukturze. | Komunikat „Error: Invalid Parameter”, nazwa nie zostaje zmieniona.        | Chrome 138, Firefox 127, Windows 10, demo 2025-07-11            | [DEF-03.png](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/2e909f2db0da4aa60173d8412e595483139c8c88/attachments/DEF-03.png)  |
| IMP-04 | Mało czytelne rozmieszczenie przycisków akcji                        | UI/UX (Mobile)   | Niski     | 1. Zaloguj się jako Admin 2. Przeglądaj różne moduły 3. Zwróć uwagę na rozmieszczenie przycisków akcji 4. Udokumentuj obserwacje nagraniem ekranu | Przejrzyste i logiczne rozmieszczenie przycisków akcji.                | Przyciski są rozmieszczone w sposób nieintuicyjny.                        | Mi Note 10 Lite, Google Chrome 138, Android 12, demo 2025-07-11 | [IMP-04.mp4](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/98bd86c857d54a5733d815a147b8dba6c1889bd0/attachments/DEF-04.mp4)  |
| IMP-06 | Brak możliwości podejrzenia hasła                                    | Login (Mobile)   | Niski     | 1. Otwórz ekran logowania 2. Wpisz hasło 3. Poszukaj opcji „pokaż hasło”                                   | Dostępny przycisk/ikona umożliwiająca podgląd hasła.                   | Brak takiej opcji – pole hasła zawsze zamaskowane.                         | Mi Note 10 Lite, Google Chrome 138, Android 12, demo 2025-07-11 | [IMP-06.jpg](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/4c90a7f596336b8a2bb23aedd5d6f5984e528652/attachments/IMP-06.jpg)  |
| IMP-07 | Brak zwijania się przycisku/menu                                     | UI/UX (Mobile)   | Niski     | 1. Otwórz aplikację 2. Kliknij przycisk/menu, który powinien się zwijać                                    | Przycisk/menu zwija się poprawnie.                                     | Przycisk się nie zwija.                                                    | Mi Note 10 Lite, Google Chrome 138, Android 12, demo 2025-07-11 | [IMP-07.mp4](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/d16a82d761244b1369203f06dc8ca313f59f2cdc/attachments/IMP-07.mp4)  |
| DEF-04 | Wideo nie dostosowuje się do rozmiaru ekranu                         | UI/UX (Mobile)   | Średni    | 1. Otwórz aplikację na urządzeniu mobilnym 2. Przejdź do ekranu z wideo 3. Obserwuj, że wideo nie zmienia rozmiaru zgodnie z ekranem | Wideo powinno automatycznie dostosowywać się do rozmiaru ekranu        | Wideo pozostaje w stałym rozmiarze i nie dostosowuje się                   | Mi Note 10 Lite, Google Chrome 138, Android 12, demo 2025-07-11 | [DEF-04.mp4](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/e4bb72eec636852cb6718fc0879313c093a54775/attachments/DEF-04.mp4)  |
| DEF-05 | Strona rozjeżdża się, elementy nachodzą na siebie                    | UI/UX (Mobile)   | Wysoki    | 1. Otwórz aplikację na urządzeniu mobilnym 2. Przeglądaj różne podstrony i sekcje 3. Obserwuj, czy elementy strony nie nachodzą na siebie i są poprawnie rozmieszczone | Wszystkie elementy strony powinny być poprawnie rozmieszczone i nie nachodzić na siebie | Elementy strony nachodzą na siebie, układ jest rozjechany                  | Mi Note 10 Lite, Google Chrome 138, Android 12, demo 2025-07-11 | [DEF-05.mp4](https://github.com/Kasper-Zdaniec/manual-testing-orangehrm/blob/55e81f83657b39c504ef05d818299e706f58064a/attachments/DEF-05.mp4)  |

### 10. Traceability (Pokrycie wymagań)

Przypadki testowe pokrywają podstawowe wymagania funkcjonalne aplikacji na podstawie eksploracji interfejsu.  
W przypadku dostępności dokumentacji wymagań możliwe jest przygotowanie macierzy traceability.

### 11. Ograniczenia i ryzyka (Test Constraints & Risks)

- Testy przeprowadzono wyłącznie na koncie Administratora – brak możliwości weryfikacji procesów dostępnych dla innych ról użytkowników (np. pracownika).
- Błąd uniemożliwiający edycję jednostki organizacyjnej blokuje pełną weryfikację CRUD w tym module.
- Brak walidacji i komunikatów może skutkować błędami użytkowników.
- Ograniczony zakres testów – nie testowano uprawnień innych ról, integracji, raportowania.

### 12. Wnioski

Aplikacja OrangeHRM Demo działa stabilnie w zakresie zarządzania pracownikami oraz umożliwia przeglądanie, dodawanie i usuwanie jednostek organizacyjnych.  
W module zarządzania strukturą organizacyjną występuje błąd uniemożliwiający edycję nazwy jednostki („Error: Invalid Parameter”), co uniemożliwia pełną weryfikację operacji CRUD.  
Na ekranie logowania (szczególnie na urządzeniach mobilnych) brakuje opcji podglądu hasła, co może utrudniać użytkownikom poprawne wpisanie hasła.  
Po edycji danych pracownika zmiany nie są widoczne bez ręcznego przeładowania strony, co może wprowadzać użytkownika w błąd.  
Dodatkowo, w interfejsie użytkownika zauważono nieintuicyjne rozmieszczenie przycisków akcji, brak zwijania się przycisków/menu na urządzeniach mobilnych, brak responsywności wideo oraz rozjeżdżanie się strony i nachodzenie elementów, co wpływa na ergonomię i nowoczesność UI.

**Załączniki:**
- Zrzuty ekranu i nagrania dokumentujące defekty i usprawnienia (np. IMP-04.mp4, IMP-06.jpg, IMP-07.mp4, DEF-04.mp4, DEF-05.mp4)
- Plik z przypadkami testowymi w formacie Markdown

Raport przygotował: Kasper Żdaniec  
W razie dodatkowych pytań lub potrzeby rozszerzenia zakresu testów – pozostaję do dyspozycji.
