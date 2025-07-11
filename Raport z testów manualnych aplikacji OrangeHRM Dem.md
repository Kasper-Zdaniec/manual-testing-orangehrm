Oczywiście, poniżej zaktualizowana wersja raportu z poprawionym imieniem i nazwiskiem testera:

# Raport z testów manualnych aplikacji OrangeHRM Demo  
**Przygotowany zgodnie z dobrymi praktykami i terminologią ISTQB**

## 1. Wprowadzenie

Celem raportu jest przedstawienie wyników testów manualnych wybranych funkcjonalności aplikacji OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/), przeprowadzonych w środowisku testowym po zalogowaniu na konto Admin. Dokument został opracowany zgodnie z zaleceniami ISTQB, z zachowaniem właściwej terminologii, struktury oraz kompletności informacji testerskich.

## 2. Zakres testów (Test Scope)

- **Moduły objęte testami:**
  - Zarządzanie pracownikami (PIM – Personal Information Management)
  - Zarządzanie urlopami (Leave)
- **Zakres funkcjonalny:** podstawowe scenariusze CRUD, składanie i obsługa wniosków urlopowych
- **Zakres nieobjęty testami:** integracje zewnętrzne, raportowanie, uprawnienia innych ról użytkowników

## 3. Środowisko testowe (Test Environment)

- **Przeglądarki:** Google Chrome (v125+), Mozilla Firefox (v127+)
- **Tryb mobilny:** Chrome DevTools – tryb responsywny
- **System operacyjny:** Windows 11
- **Dane testowe:** generowane na potrzeby testów, niepochodzące z produkcji
- **Wersja aplikacji:** aktualna wersja demo na dzień testów

## 4. Wykorzystane narzędzia

- Google Chrome, Mozilla Firefox
- Chrome DevTools (inspekcja, analiza sieci)
- Markdown (dokumentacja)
- GitHub (kontrola wersji dokumentacji)
- Zrzuty ekranu (załączniki)

## 5. Ograniczenia testów (Test Constraints)

- Brak dostępu do dokumentacji wymagań biznesowych (traceability na podstawie eksploracji)
- Brak możliwości testowania uprawnień innych ról niż Admin
- Ograniczony czas na wykonanie testów

## 6. Przypadki testowe (Test Cases) i pokrycie wymagań

| ID TC     | Warunek testowy (Test Condition)             | Kroki testowe                                    | Dane testowe                                                                                                   | Oczekiwany rezultat                    | Status  |
|-----------|----------------------------------------------|--------------------------------------------------|----------------------------------------------------------------------------------------------------------------|----------------------------------------|---------|
| TC-PIM-01 | Dodanie nowego pracownika                    | 1. PIM → Add Employee2. Wprowadź dane3. Zapisz | Imię: JanNazwisko: TestowyID: 12345Email: jan.testowy@example.comZdjęcie: testowy.jpg         | Pracownik widoczny na liście           | Sukces  |
| TC-PIM-02 | Wyszukiwanie pracownika                      | 1. Employee List2. Wyszukaj po imieniu/nazwisku | Imię: Jan, Nazwisko: Testowy                                              | Pracownik wyświetlony na liście        | Sukces  |
| TC-PIM-03 | Edycja danych pracownika                     | 1. Wybierz pracownika2. Edytuj dane3. Zapisz | Zmiana nazwiska na: Testerski                                              | Dane zaktualizowane                    | Sukces  |
| TC-PIM-04 | Usunięcie pracownika                         | 1. Wybierz pracownika2. Usuń3. Potwierdź  | Pracownik: Jan Testerski                                                   | Pracownik usunięty z listy             | Sukces  |
| TC-LEAVE-01 | Złożenie wniosku urlopowego                | 1. Leave → Apply2. Wypełnij formularz3. Złóż wniosek | Typ: Annual LeaveData od: 2025-07-15Data do: 2025-07-20           | Wniosek widoczny na liście             | Sukces  |
| TC-LEAVE-02 | Przeglądanie statusu wniosku               | 1. Leave → My Leave2. Sprawdź status          | Wniosek z TC-LEAVE-01                                                       | Status zgodny z oczekiwaniem           | Sukces  |
| TC-LEAVE-03 | Anulowanie wniosku urlopowego              | 1. Leave → My Leave2. Spróbuj anulować wniosek | Wniosek z TC-LEAVE-01                                                       | Brak opcji anulowania                  | Brak opcji  |

## 7. Dane testowe (Test Data)

- Pracownik: Imię: Jan, Nazwisko: Testowy, ID: 12345, Email: jan.testowy@example.com, Zdjęcie: testowy.jpg
- Modyfikacja: Zmiana nazwiska na „Testerski”
- Wniosek urlopowy: typ „Annual Leave”, daty 2025-07-15 do 2025-07-20

## 8. Log testowy (Test Log)

| Data        | Tester           | Moduł  | Wersja przeglądarki | Wynik testów    |
|-------------|------------------|--------|---------------------|-----------------|
| 2025-07-10  | Kasper Żdaniec   | PIM    | Chrome 125, FF 127  | Wszystkie TC ok |
| 2025-07-10  | Kasper Żdaniec   | Leave  | Chrome 125, FF 127  | TC-LEAVE-03 fail|

## 9. Wyniki testów, defekty i usprawnienia (Defects & Improvements)

### Tabela defektów i usprawnień

| ID         | Opis defektu / usprawnienia                   | Moduł       | Priorytet | Sposób raportowania defektu                  | Zrzut ekranu |
|------------|-----------------------------------------------|-------------|-----------|----------------------------------------------|--------------|
| DEF-01     | Zmiany po edycji pracownika nie są widoczne   | PIM         | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-01 |
| DEF-02     | Brak walidacji formatu zdjęcia                | PIM         | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-02 |
| IMP-01     | Brak komunikatu po edycji danych pracownika   | PIM         | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-01 |
| IMP-02     | Brak możliwości masowego usuwania pracowników | PIM         | Niski     | Zgłoszenie jako usprawnienie                 | —           |
| DEF-03     | Brak opcji anulowania wniosku urlopowego      | Leave       | Wysoki    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-03 |
| DEF-04     | Brak czytelnego komunikatu po złożeniu wniosku| Leave       | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-04 |
| IMP-03     | Brak filtrów po statusie/typie urlopu/dacie   | Leave       | Niski     | Zgłoszenie jako usprawnienie                 | —           |
| IMP-04     | Brak walidacji pól formularza urlopowego      | Leave       | Średni    | Zgłoszenie jako usprawnienie                 | Załącznik IMP-04 |
| IMP-05     | Mało czytelne rozmieszczenie przycisków akcji | UI/UX       | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-05 |
| IMP-06     | Brak responsywności UI dla urządzeń mobilnych | UI/UX       | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-06 |

## 10. Traceability (Pokrycie wymagań)

- Przypadki testowe pokrywają podstawowe wymagania funkcjonalne aplikacji na podstawie eksploracji interfejsu.
- W przypadku dostępności dokumentacji wymagań możliwe jest przygotowanie macierzy traceability.

## 11. Ograniczenia i ryzyka (Test Constraints & Risks)

- Brak możliwości anulowania wniosku urlopowego może prowadzić do błędów w ewidencji i kosztów administracyjnych.
- Brak walidacji i komunikatów może skutkować błędami użytkowników.
- Ograniczony zakres testów – nie testowano uprawnień innych ról, integracji, raportowania.

## 12. Wnioski

Aplikacja OrangeHRM Demo działa stabilnie w podstawowym zakresie, a wykryte defekty nie są krytyczne. Wdrożenie zaproponowanych usprawnień istotnie podniesie jakość produktu i satysfakcję użytkowników.  
Raport został przygotowany zgodnie z terminologią i strukturą ISTQB, z zachowaniem traceability, logu testowego, opisu środowiska, danych testowych oraz formalnego raportowania defektów.

Jestem otwarty na feedback, dalszą optymalizację procesu testowania oraz aktywny udział w rozwoju jakości oprogramowania w Państwa zespole QA.

**Załączniki:**  
- Zrzuty ekranu dokumentujące defekty i usprawnienia  
- Plik z przypadkami testowymi w formacie Markdown

Raport przygotował: **Kasper Żdaniec**

W razie dodatkowych pytań lub potrzeby rozszerzenia zakresu testów – pozostaję do dyspozycji.
