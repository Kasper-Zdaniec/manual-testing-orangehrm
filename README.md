# Raport z testów manualnych aplikacji OrangeHRM Demo  
**Przygotowany zgodnie z dobrymi praktykami i terminologią ISTQB**

## 1. Wprowadzenie

Celem raportu jest przedstawienie wyników testów manualnych wybranych funkcjonalności aplikacji OrangeHRM Demo (https://opensource-demo.orangehrmlive.com/), przeprowadzonych w środowisku testowym po zalogowaniu na konto **Admin**. Dokument został opracowany zgodnie z zaleceniami ISTQB, z zachowaniem właściwej terminologii, struktury oraz kompletności informacji testerskich.

## 2. Zakres testów (Test Scope)

- **Moduły objęte testami:**
  - Zarządzanie pracownikami (PIM – Personal Information Management)
  - Zarządzanie strukturą organizacyjną (Organization Structure)
- **Zakres funkcjonalny:** podstawowe scenariusze CRUD, zarządzanie strukturą firmy (dodawanie, edycja i usuwanie jednostek organizacyjnych)
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

| ID TC      | Warunek testowy                  | Kroki testowe                                                                                                   | Dane testowe                                      | Oczekiwany rezultat                | Status  | Komentarz                                                                                      |
|------------|----------------------------------|----------------------------------------------------------------------------------------------------------------|---------------------------------------------------|------------------------------------|---------|------------------------------------------------------------------------------------------------|
| TC-PIM-01  | Dodanie nowego pracownika        | 1. PIM → Add Employee 2. Wprowadź dane 3. Zapisz                          | Imię: Jan, Nazwisko: Testowy, ID: 12345, Zdjęcie: testowy.png           | Pracownik widoczny na liście       | Sukces  |                                                                                                 |
| TC-PIM-02  | Wyszukiwanie pracownika          | 1. Employee List 2. Wyszukaj po imieniu/nazwisku                          | Imię: Jan, Nazwisko: Testowy                                             | Pracownik wyświetlony na liście    | Sukces  |                                                                                                 |
| TC-PIM-03  | Edycja danych pracownika         | 1. Wybierz pracownika 2. Edytuj dane 3. Zapisz                            | Zmiana nazwiska na: Testerski                                            | Dane zaktualizowane                | Sukces  |                                                                                                 |
| TC-PIM-04  | Usunięcie pracownika             | 1. Przejdź do PIM → Employee List 2. Wyszukaj pracownika (np. Jan Testerski) 3. Zaznacz pracownika na liście 4. Kliknij „Delete” 5. Potwierdź operację w oknie dialogowym | Pracownik: Jan Testerski                         | Pracownik usunięty z listy         | Sukces  |                                                                                                 |
| TC-ORG-01  | Dodanie jednostki organizacyjnej | 1. Admin → Organization → Structure 2. Dodaj nową jednostkę 3. Wprowadź nazwę 4. Zapisz                        | Nazwa: Testowa Jednostka                           | Jednostka widoczna w strukturze    | Sukces  |                                                                                                 |
| TC-ORG-02  | Edycja jednostki organizacyjnej  | 1. Wybierz jednostkę 2. Edytuj nazwę 3. Zapisz                            | Nowa nazwa: Zmieniona Jednostka                    | Zaktualizowana nazwa w strukturze  | Sukces  |                                                                                                 |
| TC-ORG-03  | Usunięcie jednostki organizacyjnej | 1. Wybierz jednostkę 2. Usuń 3. Potwierdź operację                        | Jednostka: Zmieniona Jednostka                     | Jednostka usunięta ze struktury    | Sukces  |                                                                                                 |

## 7. Dane testowe (Test Data)

**Pracownik:**  
Imię: Jan, Nazwisko: Testowy, ID: 12345, Zdjęcie: testowy.png

**Modyfikacja:**  
Zmiana nazwiska na „Testerski”

**Jednostka organizacyjna:**  
Nazwa: Testowa Jednostka  
Nowa nazwa: Zmieniona Jednostka

## 8. Log testowy (Test Log)

| Data        | Tester           | Moduł         | Wersja przeglądarki | TC                | Wynik      | Komentarz                                                                 |
|-------------|------------------|--------------|---------------------|-------------------|------------|---------------------------------------------------------------------------|
| 2025-07-10  | Kasper Żdaniec   | PIM          | Chrome 125, FF 127  | Wszystkie         | OK         | Wszystkie przypadki PIM zakończone sukcesem                               |
| 2025-07-11  | Kasper Żdaniec   | Organization | Chrome 125, FF 127  | TC-ORG-01         | OK         | Dodanie jednostki organizacyjnej przebiegło prawidłowo                    |
| 2025-07-11  | Kasper Żdaniec   | Organization | Chrome 125, FF 127  | TC-ORG-02         | OK         | Edycja nazwy jednostki przebiegła prawidłowo                              |
| 2025-07-11  | Kasper Żdaniec   | Organization | Chrome 125, FF 127  | TC-ORG-03         | OK         | Usunięcie jednostki przebiegło prawidłowo                                 |

## 9. Wyniki testów, defekty i usprawnienia (Defects & Improvements)

### Tabela defektów i usprawnień

| ID         | Opis defektu / usprawnienia                   | Moduł       | Priorytet | Sposób raportowania defektu                  | Zrzut ekranu         |
|------------|-----------------------------------------------|-------------|-----------|----------------------------------------------|----------------------|
| DEF-01     | Zmiany po edycji pracownika nie są widoczne   | PIM         | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-01     |
| DEF-02     | Brak walidacji formatu zdjęcia                | PIM         | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-02     |
| IMP-01     | Brak komunikatu po edycji danych pracownika   | PIM         | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-01     |
| IMP-02     | Brak możliwości masowego usuwania pracowników | PIM         | Niski     | Zgłoszenie jako usprawnienie                 | —                   |
| DEF-03     | Brak walidacji przy edycji jednostki organizacyjnej | Organization | Średni    | Zgłoszenie przez system bugtrackingowy       | Załącznik DEF-03     |
| IMP-03     | Brak możliwości dodania opisu jednostki       | Organization | Niski     | Zgłoszenie jako usprawnienie                 | —                   |
| IMP-04     | Mało czytelne rozmieszczenie przycisków akcji | UI/UX       | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-04     |
| IMP-05     | Brak responsywności UI dla urządzeń mobilnych | UI/UX       | Niski     | Zgłoszenie jako usprawnienie                 | Załącznik IMP-05     |

## 10. Traceability (Pokrycie wymagań)

- Przypadki testowe pokrywają podstawowe wymagania funkcjonalne aplikacji na podstawie eksploracji interfejsu.
- W przypadku dostępności dokumentacji wymagań możliwe jest przygotowanie macierzy traceability.

## 11. Ograniczenia i ryzyka (Test Constraints & Risks)

- Testy przeprowadzono wyłącznie na koncie Administratora – brak możliwości weryfikacji procesów dostępnych dla innych ról użytkowników (np. pracownika).
- Brak walidacji i komunikatów może skutkować błędami użytkowników.
- Ograniczony zakres testów – nie testowano uprawnień innych ról, integracji, raportowania.

## 12. Wnioski

Aplikacja OrangeHRM Demo działa stabilnie w zakresie zarządzania pracownikami oraz strukturą organizacyjną, a wykryte defekty nie są krytyczne dla podstawowej pracy tych modułów.  
Wdrożenie zaproponowanych usprawnień istotnie podniesie jakość produktu i satysfakcję użytkowników.  
Raport został przygotowany zgodnie z terminologią i strukturą ISTQB, z zachowaniem traceability, logu testowego, opisu środowiska, danych testowych oraz formalnego raportowania defektów.

**Załączniki:**  
- Zrzuty ekranu dokumentujące defekty i usprawnienia  
- Plik z przypadkami testowymi w formacie Markdown

Raport przygotował: **Kasper Żdaniec**

W razie dodatkowych pytań lub potrzeby rozszerzenia zakresu testów – pozostaję do dyspozycji.
