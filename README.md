# Raport z testów manualnych aplikacji OrangeHRM Demo  
*Przygotowany zgodnie z dobrymi praktykami i terminologią ISTQB*

## 1. Wprowadzenie

Celem raportu jest przedstawienie wyników testów manualnych wybranych funkcjonalności aplikacji OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/), przeprowadzonych w środowisku testowym na koncie **Admin**. Dokument został opracowany zgodnie z zaleceniami ISTQB, z zachowaniem właściwej terminologii, struktury oraz kompletności informacji testerskich.

## 2. Zakres testów (Test Scope)

- **Moduły objęte testami:**
  - Zarządzanie pracownikami (PIM – Personal Information Management)
  - Zarządzanie strukturą organizacyjną (Organization Structure)
- **Zakres funkcjonalny:** podstawowe scenariusze CRUD, zarządzanie strukturą firmy (dodawanie, edycja, usuwanie i przeglądanie jednostek organizacyjnych)
- **Zakres nieobjęty testami:** integracje zewnętrzne, raportowanie, uprawnienia innych ról użytkowników

## 3. Środowisko testowe (Test Environment)

- **Przeglądarki:** Google Chrome (v125+), Mozilla Firefox (v127+)
- **Tryb mobilny:** Chrome DevTools – tryb responsywny
- **System operacyjny:** Windows 10
- **Dane testowe:** generowane na potrzeby testów, niepochodzące z produkcji
- **Wersja aplikacji:** aktualna wersja demo na dzień testów

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
| TC-ORG-03  | Usunięcie jednostki organizacyjnej    | 1. Admin → Organization → Structure 2. Kliknij „Edit” 3. Wybierz jednostkę 4. Usuń 5. Potwierdź operację       | Jednostka: Zmieniona Jednostka                     | Jednostka usunięta ze struktury    | Pominięty | Nie można przetestować z powodu nieudanego TC-ORG-02.                                           |

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
| 2025-07-11  | Kasper Żdaniec   | Organization | TC-ORG-03  | Pominięty | Nie można przetestować z powodu nieudanego TC-ORG-02                       |

## 9. Wyniki testów, defekty i usprawnienia (Defects & Improvements)

### Tabela defektów i usprawnień

| ID         | Opis defektu / usprawnienia                   | Moduł       | Priorytet | Sposób raportowania defektu                  | Zrzut ekranu         |
|------------|-----------------------------------------------|-------------|-----------|----------------------------------------------|----------------------|
| DEF-01     | Zmiany po edycji pracownika nie są widoczne   | PIM         | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-01     |
| DEF-02     | Brak walidacji formatu zdjęcia                | PIM         | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-02     |
| IMP-01     | Brak komunikatu po edycji danych pracownika   | PIM         | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-01     |
| IMP-02     | Brak możliwości masowego usuwania pracowników | PIM         | Niski     | Zgłoszenie jako usprawnienie                 | —                   |
| DEF-03     | Błąd „Error: Invalid Parameter” przy edycji jednostki organizacyjnej | Organization | Wysoki    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-03     |
| IMP-03     | Brak możliwości dodania opisu jednostki       | Organization | Niski     | Zgłoszenie jako usprawnienie                 | —                   |
| IMP-04     | Mało czytelne rozmieszczenie przycisków akcji | UI/UX       | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-04     |
| IMP-05     | Brak responsywności UI dla urządzeń mobilnych | UI/UX       | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-05     |

## 10. Traceability (Pokrycie wymagań)

- Przypadki testowe pokrywają podstawowe wymagania funkcjonalne aplikacji na podstawie eksploracji interfejsu.
- W przypadku dostępności dokumentacji wymagań możliwe jest przygotowanie macierzy traceability.

## 11. Ograniczenia i ryzyka (Test Constraints & Risks)

- Testy przeprowadzono wyłącznie na koncie Administratora – brak możliwości weryfikacji procesów dostępnych dla innych ról użytkowników (np. pracownika).
- Błąd uniemożliwiający edycję jednostki organizacyjnej blokuje dalsze testowanie tego obszaru.
- Brak walidacji i komunikatów może skutkować błędami użytkowników.
- Ograniczony zakres testów – nie testowano uprawnień innych ról, integracji, raportowania.

## 12. Wnioski

Aplikacja OrangeHRM Demo działa stabilnie w zakresie zarządzania pracownikami oraz umożliwia przeglądanie i dodawanie jednostek organizacyjnych.  
W module zarządzania strukturą organizacyjną występuje błąd uniemożliwiający edycję nazwy jednostki („Error: Invalid Parameter”), co uniemożliwia pełną weryfikację operacji CRUD.  
Wdrożenie zaproponowanych usprawnień istotnie podniesie jakość produktu i satysfakcję użytkowników.  
Raport został przygotowany zgodnie z terminologią i strukturą ISTQB, z zachowaniem traceability, logu testowego, opisu środowiska, danych testowych oraz formalnego raportowania defektów.

**Załączniki:**  
- Zrzuty ekranu dokumentujące defekty i usprawnienia  
- Plik z przypadkami testowymi w formacie Markdown

Raport przygotował: **Kasper Żdaniec**

W razie dodatkowych pytań lub potrzeby rozszerzenia zakresu testów – pozostaję do dyspozycji.
