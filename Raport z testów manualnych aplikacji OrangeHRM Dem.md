# Raport z testów manualnych aplikacji OrangeHRM Demo

## Wprowadzenie

Raport został przygotowany zgodnie z dobrymi praktykami ISTQB oraz z wykorzystaniem narzędzi testerskich: Google Chrome, Mozilla Firefox, Chrome DevTools, notatki w Markdown, zrzuty ekranu (dołączone w załączniku) oraz GitHub do kontroli wersji dokumentacji.  
Celem testów była analiza jakości działania oraz użyteczności wybranych funkcjonalności aplikacji OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/) w środowisku testowym, po zalogowaniu na konto Admin (login: Admin, hasło: admin123).

Wybrane do analizy moduły:
- **Zarządzanie pracownikami (PIM – Personal Information Management)**
- **Zarządzanie urlopami (Leave)**

Testy przeprowadzono metodycznie, z uwzględnieniem aspektów funkcjonalnych, UI/UX, priorytetyzacji błędów oraz potencjalnych ryzyk biznesowych.

## Narzędzia i techniki testowania

- **Przeglądarki:** Google Chrome (v125+), Mozilla Firefox (v127+)
- **Tryb mobilny:** Testy w trybie responsywnym Chrome DevTools
- **Narzędzia deweloperskie:** Chrome DevTools (analiza sieci, inspekcja elementów)
- **Dokumentacja:** Markdown, zrzuty ekranu (załącznik), kontrola wersji (GitHub)
- **Metodyka:** Testowanie eksploracyjne, testy pozytywne i negatywne, zgodność z ISTQB

## Przypadki testowe (Test Cases)

### 1. Zarządzanie pracownikami (PIM)

| ID TC     | Scenariusz                    | Kroki testowe                                                                 | Oczekiwany rezultat                    | Status  |
|-----------|-------------------------------|-------------------------------------------------------------------------------|----------------------------------------|---------|
| TC-PIM-01 | Dodanie nowego pracownika     | 1. PIM → Add Employee2. Wprowadź dane3. Zapisz                        | Pracownik widoczny na liście           | Sukces  |
| TC-PIM-02 | Wyszukiwanie pracownika       | 1. Employee List2. Wyszukaj po imieniu/nazwisku                           | Pracownik wyświetlony na liście        | Sukces  |
| TC-PIM-03 | Edycja danych pracownika      | 1. Wybierz pracownika2. Edytuj dane3. Zapisz                          | Dane zaktualizowane                    | Sukces  |
| TC-PIM-04 | Usunięcie pracownika          | 1. Wybierz pracownika2. Usuń3. Potwierdź                              | Pracownik usunięty z listy             | Sukces  |

### 2. Zarządzanie urlopami (Leave)

| ID TC        | Scenariusz                    | Kroki testowe                                                                 | Oczekiwany rezultat                    | Status      |
|--------------|-------------------------------|-------------------------------------------------------------------------------|----------------------------------------|-------------|
| TC-LEAVE-01  | Złożenie wniosku urlopowego   | 1. Leave → Apply2. Wypełnij formularz3. Złóż wniosek                  | Wniosek widoczny na liście             | Sukces      |
| TC-LEAVE-02  | Przeglądanie statusu wniosku  | 1. Leave → My Leave2. Sprawdź status                                      | Status zgodny z oczekiwaniem           | Sukces      |
| TC-LEAVE-03  | Anulowanie wniosku urlopowego | 1. Leave → My Leave2. Spróbuj anulować wniosek                            | Brak opcji anulowania                  | Brak opcji  |

## Wyniki testów, błędy i usprawnienia

### Tabela podsumowująca błędy, usprawnienia i priorytety

| ID         | Opis problemu / Usprawnienia                                  | Moduł       | Priorytet | Propozycja rozwiązania                            | Zrzut ekranu |
|------------|---------------------------------------------------------------|-------------|-----------|---------------------------------------------------|--------------|
| BUG-01     | Zmiany po edycji pracownika nie są widoczne od razu           | PIM         | Średni    | Automatyczne odświeżanie listy po edycji          | Tak          |
| BUG-02     | Brak walidacji formatu zdjęcia przy dodawaniu pracownika      | PIM         | Średni    | Ograniczenie uploadu do JPG/PNG                   | Tak          |
| IMP-01     | Brak komunikatu po edycji danych pracownika                   | PIM         | Niski     | Dodanie potwierdzenia operacji                    | Tak          |
| IMP-02     | Brak możliwości masowego usuwania pracowników                 | PIM         | Niski     | Dodanie opcji multi-select i usuwania             | Nie          |
| BUG-03     | Brak opcji anulowania złożonego wniosku urlopowego            | Leave       | Wysoki    | Dodanie funkcji anulowania                        | Tak          |
| BUG-04     | Brak czytelnego komunikatu po złożeniu wniosku urlopowego     | Leave       | Średni    | Wyświetlanie potwierdzenia operacji               | Tak          |
| IMP-03     | Brak filtrów po statusie/typie urlopu/dacie                   | Leave       | Niski     | Rozbudowa filtrów w module My Leave               | Nie          |
| IMP-04     | Brak walidacji pól formularza urlopowego                      | Leave       | Średni    | Dodanie walidacji dat i wymaganych pól            | Tak          |
| IMP-05     | Mało czytelne rozmieszczenie przycisków akcji                 | UI/UX       | Niski     | Ujednolicenie rozmieszczenia i stylu przycisków   | Tak          |
| IMP-06     | Brak responsywności UI dla urządzeń mobilnych                 | UI/UX       | Niski     | Wprowadzenie responsywnego designu                | Tak          |

## Ryzyka i rekomendacje

- **Ryzyko biznesowe:** Brak możliwości anulowania wniosku urlopowego może prowadzić do błędnych wpisów w ewidencji i niepotrzebnych kosztów administracyjnych.
- **Ryzyko użyteczności:** Brak walidacji i czytelnych komunikatów może zniechęcać użytkowników i prowadzić do błędów w danych.
- **Rekomendacja:** Priorytetyzować poprawę funkcjonalności o największym wpływie na użytkownika końcowego (np. anulowanie wniosków, walidacja, komunikaty).

## Dodatkowe obserwacje

- Interfejs aplikacji jest intuicyjny, jednak komunikaty systemowe powinny być bardziej widoczne i informacyjne.
- Testy przeprowadzono na dwóch przeglądarkach oraz w trybie mobilnym – aplikacja wymaga poprawy responsywności.
- Rozmieszczenie przycisków akcji bywa niespójne, co może utrudniać szybkie wykonywanie operacji.

## Wnioski

Aplikacja OrangeHRM Demo działa stabilnie i spełnia podstawowe wymagania biznesowe. Wykryte błędy nie są krytyczne, lecz wdrożenie zaproponowanych usprawnień znacząco podniesie jakość produktu oraz satysfakcję użytkowników. W przypadku ograniczonego czasu testowania, rekomenduję skupienie się na funkcjonalnościach o najwyższym wpływie na użytkownika (np. obsługa wniosków urlopowych, walidacja danych).

Raport został przygotowany z dbałością o szczegóły, zgodnie z najlepszymi praktykami testerskimi i z wykorzystaniem narzędzi do dokumentacji oraz kontroli wersji. Jestem otwarty na feedback, dalszą optymalizację procesu testowania oraz aktywny udział w rozwoju jakości oprogramowania w Państwa zespole QA.

**Załączniki:**  
- Zrzuty ekranu dokumentujące błędy i usprawnienia  
- Plik z przypadkami testowymi w formacie Markdown

W razie dodatkowych pytań lub potrzeby rozszerzenia zakresu testów – pozostaję do dyspozycji.
