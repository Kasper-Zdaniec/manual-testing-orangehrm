# Raport z testów manualnych aplikacji OrangeHRM Demo

## Wstęp

Celem testów było sprawdzenie wybranych funkcjonalności demo systemu HR dostępnego pod adresem https://opensource-demo.orangehrmlive.com/. Testy przeprowadzono po zalogowaniu się na konto Admin (login: Admin, hasło: admin123). Wybrano dwie funkcjonalności:

- Zarządzanie użytkownikami (Admin → User Management → Users)
- Moduł urlopów (Leave)

Poniżej znajduje się opis przeprowadzonych testów, wykryte błędy oraz propozycje usprawnień.

## Funkcjonalność 1: Zarządzanie użytkownikami

### Zakres testów

- Wyświetlanie listy użytkowników
- Filtrowanie i wyszukiwanie użytkowników
- Dodawanie nowego użytkownika
- Edycja istniejącego użytkownika
- Usuwanie użytkownika

### Wyniki testów

| Testowana akcja              | Wynik         | Uwagi/Błędy                                                                                         |
|------------------------------|---------------|-----------------------------------------------------------------------------------------------------|
| Wyświetlanie listy           | OK            | Lista ładuje się poprawnie                                                                          |
| Filtrowanie po roli          | OK            | Filtrowanie działa zgodnie z oczekiwaniami                                                          |
| Wyszukiwanie po nazwie       | OK            | Wyszukiwanie działa, ale nie rozróżnia wielkości liter                                              |
| Dodawanie użytkownika        | Błąd          | Po dodaniu użytkownika nie zawsze pojawia się komunikat o sukcesie, czasem nie odświeża się lista   |
| Edycja użytkownika           | OK            | Edycja przebiega poprawnie                                                                          |
| Usuwanie użytkownika         | OK            | Użytkownik zostaje usunięty, pojawia się komunikat potwierdzający                                   |

#### Znalezione błędy

- Brak odświeżenia listy po dodaniu użytkownika – konieczne ręczne odświeżenie strony.
- Brak jednoznacznego komunikatu o sukcesie po dodaniu użytkownika.

#### Propozycje usprawnień (UI/UX, funkcjonalne)

- Automatyczne odświeżanie listy użytkowników po dodaniu nowego wpisu.
- Wyraźny, widoczny komunikat o sukcesie po każdej operacji (dodanie, edycja, usunięcie).
- Dodanie możliwości sortowania po kolumnach (np. po nazwie, statusie).
- Umożliwienie wyszukiwania z rozróżnieniem wielkości liter.

## Funkcjonalność 2: Moduł urlopów (Leave)

### Zakres testów

- Składanie wniosku urlopowego
- Przeglądanie historii wniosków
- Akceptacja/odrzucenie wniosku (rola Admin)
- Filtrowanie wniosków

### Wyniki testów

| Testowana akcja               | Wynik         | Uwagi/Błędy                                                                                      |
|-------------------------------|---------------|--------------------------------------------------------------------------------------------------|
| Składanie wniosku urlopowego  | OK            | Wniosek zostaje złożony, pojawia się komunikat o sukcesie                                        |
| Przeglądanie historii         | OK            | Historia wyświetla się poprawnie                                                                 |
| Filtrowanie po statusie       | OK            | Filtrowanie działa, ale nie można filtrować po kilku statusach jednocześnie                      |
| Akceptacja/odrzucenie wniosku | Błąd          | Po akceptacji/odrzuceniu nie zawsze aktualizuje się status na liście bez odświeżenia strony      |

#### Znalezione błędy

- Brak automatycznej aktualizacji statusu po akceptacji/odrzuceniu wniosku urlopowego.
- Brak możliwości filtrowania po kilku statusach jednocześnie.

#### Propozycje usprawnień (UI/UX, funkcjonalne)

- Automatyczna aktualizacja statusu wniosku na liście po akcji akceptacji/odrzucenia.
- Dodanie możliwości filtrowania po wielu statusach jednocześnie.
- Umożliwienie masowej akceptacji/odrzucenia wniosków.
- Lepsze wyróżnienie statusów kolorami dla szybszej identyfikacji.

## Podsumowanie

Testy wykazały, że aplikacja jest intuicyjna i większość podstawowych funkcji działa poprawnie. Wskazane błędy dotyczą głównie braku automatycznego odświeżania danych oraz niejednoznacznych komunikatów po operacjach. Propozycje usprawnień dotyczą zarówno warstwy funkcjonalnej, jak i UI/UX, co może pozytywnie wpłynąć na komfort użytkowania aplikacji.
