# Raport z testów manualnych aplikacji OrangeHRM Demo  
*Przygotowany zgodnie z dobrymi praktykami i terminologią ISTQB*

## 1. Wprowadzenie

Celem raportu jest przedstawienie wyników testów manualnych wybranych funkcjonalności aplikacji OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/), przeprowadzonych w środowisku testowym na koncie **Admin**. Dokument został opracowany zgodnie z zaleceniami ISTQB, z zachowaniem właściwej terminologii, struktury oraz kompletności informacji testerskich.

## 2. Zakres testów (Test Scope)

- **Moduły objęte testami:**
  - Zarządzanie pracownikami (PIM – Personal Information Management)
  - Zarządzanie strukturą organizacyjną (Organization Structure)
- **Zakres funkcjonalny:** podstawowe scenariusze CRUD, zarządzanie strukturą firmy (przeglądanie, dodawanie, edycja i usuwanie jednostek organizacyjnych)
- **Zakres nieobjęty testami:** integracje zewnętrzne, raportowanie, uprawnienia innych ról użytkowników

## 3. Środowisko testowe (Test Environment)

- **Przeglądarki:** Google Chrome (v125+), Mozilla Firefox (v127+)
- **Tryb mobilny:** Chrome DevTools – tryb responsywny
- **System operacyjny:** Windows 10
- **Dane testowe:** generowane na potrzeby testów, niepochodzące z produkcji
- **Wersja aplikacji:** aktualna wersja demo na dzień testów (11.07.2025)

## 4. Wykorzystane narzędzia

- Google Chrome, Mozilla Firefox
- Chrome DevTools (inspekcja, analiza sieci)
- Markdown (dokumentacja)
- GitHub (kontrola wersji dokumentacji)
- Zrzuty ekranu (załączniki)

## 5. Ograniczenia testów (Test Constraints)

- Testy przeprowadzono wyłącznie na koncie Administratora – brak możliwości weryfikacji procesów dostępnych dla innych ról użytkowników (np. pracownika).
- Brak dostępu do dokumentacji wymagań biznesowych (traceability na podstawie eksploracji).
- Ograniczony czas na wykonanie testów.

## 6. Przypadki testowe (Test Cases) i pokrycie wymagań

| ID TC      | Warunek testowy                       | Kroki testowe                                                                                                   | Dane testowe                                      | Oczekiwany rezultat                | Status    | Komentarz                                                                                      |
|------------|---------------------------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------------------------|------------------------------------|-----------|------------------------------------------------------------------------------------------------|
| TC-PIM-01  | Dodanie nowego pracownika             | 1. PIM → Add Employee 2. Wprowadź dane 3. Zapisz                          | Imię: Jan, Nazwisko: Testowy, ID: 12345, Zdjęcie: testowy.png           | Pracownik widoczny na liście       | Sukces    |                                                                                                 |
| TC-PIM-02  | Wyszukiwanie pracownika               | 1. Employee List 2. Wyszukaj po imieniu/nazwisku                          | Imię: Jan, Nazwisko: Testowy                                             | Pracownik wyświetlony na liście    | Sukces    |                                                                                                 |
| TC-PIM-03  | Edycja danych pracownika              | 1. Wybierz pracownika 2. Edytuj dane 3. Zapisz                            | Zmiana nazwiska na: Testerski                                            | Dane zaktualizowane                | Sukces    |                                                                                                 |
| TC-PIM-04  | Usunięcie pracownika                  | 1. Przejdź do PIM → Employee List 2. Wyszukaj pracownika (np. Jan Testerski) 3. Zaznacz pracownika na liście 4. Kliknij „Delete” 5. Potwierdź operację w oknie dialogowym | Pracownik: Jan Testerski                         | Pracownik usunięty z listy         | Sukces    |                                                                                                 |
| TC-ORG-00  | Przeglądanie struktury organizacyjnej | 1. Admin → Organization → Structure 2. Sprawdź, czy wyświetlają się istniejące jednostki organizacyjne         | —                                                | Lista jednostek widoczna w strukturze | Sukces    | Struktura organizacyjna wyświetla się poprawnie po wejściu w moduł                              |
| TC-ORG-01  | Dodanie jednostki organizacyjnej      | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Dodaj nową jednostkę 4. Wprowadź nazwę 5. Zapisz      | Nazwa: Testowa Jednostka                          | Jednostka widoczna w strukturze    | Sukces    | Dodanie możliwe po wcześniejszym kliknięciu „Edit”                                              |
| TC-ORG-02  | Edycja jednostki organizacyjnej       | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Wybierz jednostkę 4. Edytuj nazwę 5. Zapisz           | Zmiana nazwy: z „Testowa Jednostka” na „Zmieniona Jednostka” | Zaktualizowana nazwa w strukturze  | Nieudany  | Komunikat „Error: Invalid Parameter” po próbie zapisania – zmiana nie jest możliwa.             |
| TC-ORG-03  | Usunięcie jednostki organizacyjnej    | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Wybierz jednostkę 4. Usuń 5. Potwierdź operację       | Jednostka: Testowa Jednostka                       | Jednostka usunięta ze struktury    | Sukces    | Usunięcie możliwe bezpośrednio po utworzeniu jednostki, niezależnie od błędu edycji             |

## 7. Dane testowe (Test Data)

**Pracownik:**  
Imię: Jan, Nazwisko: Testowy, ID: 12345, Zdjęcie: testowy.png

**Modyfikacja:**  
Zmiana nazwiska na „Testerski”

**Jednostka organizacyjna:**  
Nazwa: Testowa Jednostka  
Nowa nazwa: Zmieniona Jednostka

## 8. Log testowy (Test Log)

| Data        | Tester           | Moduł         | TC         | Wynik      | Komentarz                                                                 |
|-------------|------------------|--------------|------------|-----------|---------------------------------------------------------------------------|
| 2025-07-10  | Kasper Żdaniec   | PIM          | Wszystkie  | OK        | Wszystkie przypadki PIM zakończone sukcesem                               |
| 2025-07-11  | Kasper Żdaniec   | Organization | TC-ORG-00  | OK        | Struktura organizacyjna wyświetla się poprawnie                           |
| 2025-07-11  | Kasper Żdaniec   | Organization | TC-ORG-01  | OK        | Dodanie jednostki organizacyjnej po kliknięciu „Edit” przebiegło prawidłowo|
| 2025-07-11  | Kasper Żdaniec   | Organization | TC-ORG-02  | Fail      | Komunikat „Error: Invalid Parameter” po próbie zmiany nazwy jednostki      |
| 2025-07-11  | Kasper Żdaniec   | Organization | TC-ORG-03  | OK        | Usunięcie jednostki organizacyjnej przebiegło prawidłowo                   |

## 9. Wyniki testów, defekty i usprawnienia (Defects & Improvements)

### Tabela defektów i usprawnień

| ID         | Opis defektu / usprawnienia                   | Moduł       | Priorytet | Kroki do odtworzenia                                                                                                               | Oczekiwany rezultat                                                      | Rzeczywisty rezultat                                                     | Środowisko                                   | Załącznik         |
|------------|-----------------------------------------------|-------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|---------------------------------------------------------------------------|-----------------------------------------------|-------------------|
| DEF-01     | Zmiany po edycji pracownika nie są widoczne   | PIM         | Średni    | 1. Zaloguj się jako Admin 2. Przejdź do PIM 3. Edytuj dane pracownika 4. Zapisz 5. Sprawdź widoczność zmian                        | Dane pracownika powinny być zaktualizowane i widoczne po zapisaniu        | Zmiany nie są widoczne po zapisaniu                                       | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | DEF-01.png        |
| DEF-02     | Brak walidacji formatu zdjęcia                | PIM         | Średni    | 1. Zaloguj się jako Admin 2. Dodaj pracownika 3. Załaduj plik o niepoprawnym formacie 4. Zapisz                                    | System powinien odrzucić niepoprawny format pliku i wyświetlić komunikat  | System akceptuje każdy format pliku bez walidacji                          | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | DEF-02.png        |
| IMP-01     | Brak komunikatu po edycji danych pracownika   | PIM         | Niski     | 1. Zaloguj się jako Admin 2. Przejdź do PIM 3. Edytuj dane pracownika 4. Zapisz                                                    | System powinien wyświetlić komunikat potwierdzający zapisanie zmian        | Brak komunikatu po zapisaniu zmian                                         | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | IMP-01.png        |
| IMP-02     | Brak możliwości masowego usuwania pracowników | PIM         | Niski     | 1. Zaloguj się jako Admin 2. Przejdź do PIM 3. Spróbuj zaznaczyć wielu pracowników i usunąć ich jednocześnie                       | Możliwość zaznaczenia i usunięcia wielu pracowników naraz                  | Brak takiej możliwości                                                      | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | —                 |
| DEF-03     | Błąd „Error: Invalid Parameter” przy edycji jednostki organizacyjnej | Organization | Wysoki    | 1. Zaloguj się jako Admin 2. Przejdź do Admin → Organization → Structure 3. Kliknij „Edit” 4. Wybierz jednostkę 5. Zmień nazwę 6. Zapisz | Nazwa jednostki powinna zostać zaktualizowana i widoczna w strukturze      | Komunikat „Error: Invalid Parameter”, nazwa nie zostaje zmieniona           | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | DEF-03.png        |
| IMP-03     | Brak możliwości dodania opisu jednostki       | Organization | Niski     | 1. Zaloguj się jako Admin 2. Przejdź do Organization Structure 3. Spróbuj dodać opis do jednostki                                  | Możliwość dodania opisu do jednostki organizacyjnej                        | Brak pola lub opcji dodania opisu                                           | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | —                 |
| IMP-04     | Mało czytelne rozmieszczenie przycisków akcji | UI/UX       | Niski     | 1. Zaloguj się jako Admin 2. Przeglądaj różne moduły 3. Zwróć uwagę na rozmieszczenie przycisków akcji                             | Przejrzyste i logiczne rozmieszczenie przycisków akcji                      | Przyciski są rozmieszczone w sposób nieintuicyjny                           | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | IMP-04.png        |
| IMP-05     | Brak responsywności UI dla urządzeń mobilnych | UI/UX       | Niski     | 1. Otwórz aplikację w trybie mobilnym (np. Chrome DevTools) 2. Sprawdź wygląd i funkcjonalność UI                                  | Interfejs powinien być responsywny i czytelny na urządzeniach mobilnych     | UI nie dostosowuje się poprawnie do widoku mobilnego                        | Chrome 125, Firefox 127, Windows 10, demo 2025-07-11 | IMP-05.png        |

## 10. Traceability (Pokrycie wymagań)

- Przypadki testowe pokrywają podstawowe wymagania funkcjonalne aplikacji na podstawie eksploracji interfejsu.
- W przypadku dostępności dokumentacji wymagań możliwe jest przygotowanie macierzy traceability.

## 11. Ograniczenia i ryzyka (Test Constraints & Risks)

- Testy przeprowadzono wyłącznie na koncie Administratora – brak możliwości weryfikacji procesów dostępnych dla innych ról użytkowników (np. pracownika).
- Błąd uniemożliwiający edycję jednostki organizacyjnej blokuje pełną weryfikację CRUD w tym module.
- Brak walidacji i komunikatów może skutkować błędami użytkowników.
- Ograniczony zakres testów – nie testowano uprawnień innych ról, integracji, raportowania.

## 12. Wnioski

Aplikacja OrangeHRM Demo działa stabilnie w zakresie zarządzania pracownikami oraz umożliwia przeglądanie, dodawanie i usuwanie jednostek organizacyjnych.  
W module zarządzania strukturą organizacyjną występuje błąd uniemożliwiający edycję nazwy jednostki („Error: Invalid Parameter”), co uniemożliwia pełną weryfikację operacji CRUD.  
Raport został przygotowany zgodnie z terminologią i strukturą ISTQB, z zachowaniem traceability, logu testowego, opisu środowiska, danych testowych oraz formalnego raportowania defektów.

**Załączniki:**  
- Zrzuty ekranu dokumentujące defekty i usprawnienia  
- Plik z przypadkami testowymi w formacie Markdown

Raport przygotował: **Kasper Żdaniec**

W razie dodatkowych pytań lub potrzeby rozszerzenia zakresu testów – pozostaję do dyspozycji.
