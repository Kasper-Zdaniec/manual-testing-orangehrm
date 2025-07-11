# Raport z testów manualnych aplikacji OrangeHRM Demo

## Wprowadzenie

Celem testów było sprawdzenie wybranych funkcjonalności aplikacji OrangeHRM Demo dostępnej pod adresem https://opensource-demo.orangehrmlive.com/. Testy zostały przeprowadzone po zalogowaniu się na konto Admin (login: Admin, hasło: admin123).

Wybrałem następujące dwie funkcjonalności do testów:
- Zarządzanie pracownikami (PIM – Personal Information Management)
- Zarządzanie urlopami (Leave)

## 1. Funkcjonalność: Zarządzanie pracownikami (PIM)

### Zakres testów

- Dodawanie nowego pracownika
- Wyszukiwanie pracownika
- Edycja danych pracownika
- Usuwanie pracownika

### Przebieg testów

1. **Dodawanie pracownika**
   - Przejście do sekcji PIM → Add Employee
   - Wprowadzenie danych: imię, nazwisko, upload zdjęcia
   - Zapisanie pracownika

2. **Wyszukiwanie pracownika**
   - Wyszukiwanie po imieniu/nazwisku w sekcji Employee List

3. **Edycja danych**
   - Edycja danych istniejącego pracownika (np. zmiana nazwiska)

4. **Usuwanie pracownika**
   - Usunięcie pracownika z listy

### Wyniki i znalezione błędy

| Testowany scenariusz       | Wynik      | Opis błędu/uwaga                                                                 |
|----------------------------|------------|----------------------------------------------------------------------------------|
| Dodawanie pracownika       | Sukces     | Brak błędów krytycznych                                                          |
| Wyszukiwanie pracownika    | Sukces     | Brak błędów                                                                      |
| Edycja danych pracownika   | Sukces     | Po edycji czasem wymagane jest ponowne odświeżenie strony, by zobaczyć zmiany    |
| Usuwanie pracownika        | Sukces     | Brak błędów                                                                      |

#### Znalezione bugi

- Po edycji danych pracownika, zmiany nie zawsze są widoczne od razu – wymagane jest odświeżenie strony.
- Brak walidacji formatu zdjęcia – można dodać plik o nieprawidłowym formacie.

#### Propozycje usprawnień (UI/UX, funkcjonalne)

- Dodanie komunikatu potwierdzającego pomyślną edycję danych.
- Automatyczne odświeżanie listy pracowników po edycji/usunięciu.
- Ograniczenie typów plików możliwych do uploadu jako zdjęcie.

## 2. Funkcjonalność: Zarządzanie urlopami (Leave)

### Zakres testów

- Składanie wniosku urlopowego
- Przeglądanie statusu wniosku
- Anulowanie wniosku

### Przebieg testów

1. **Składanie wniosku urlopowego**
   - Przejście do sekcji Leave → Apply
   - Wypełnienie formularza (typ urlopu, daty)
   - Złożenie wniosku

2. **Przeglądanie statusu**
   - Leave → My Leave
   - Sprawdzenie statusu złożonego wniosku

3. **Anulowanie wniosku**
   - Próba anulowania złożonego wniosku

### Wyniki i znalezione błędy

| Testowany scenariusz         | Wynik      | Opis błędu/uwaga                                                               |
|------------------------------|------------|--------------------------------------------------------------------------------|
| Składanie wniosku urlopowego | Sukces     | Brak błędów krytycznych                                                        |
| Przeglądanie statusu         | Sukces     | Brak błędów                                                                    |
| Anulowanie wniosku           | Brak opcji | Brak widocznej opcji anulowania wniosku po złożeniu                            |

#### Znalezione bugi

- Brak możliwości anulowania złożonego wniosku urlopowego przez użytkownika.
- Po złożeniu wniosku nie pojawia się czytelny komunikat potwierdzający operację.

#### Propozycje usprawnień (UI/UX, funkcjonalne)

- Dodanie funkcji anulowania złożonego wniosku urlopowego.
- Wyświetlanie komunikatu potwierdzającego złożenie wniosku.
- Umożliwienie filtrowania wniosków po statusie, typie urlopu, dacie.

## Podsumowanie

Testowane funkcjonalności działają poprawnie w podstawowym zakresie, jednak zauważono kilka drobnych błędów oraz możliwości usprawnień, szczególnie w zakresie przejrzystości komunikatów oraz obsługi typowych scenariuszy użytkownika (odświeżanie danych, anulowanie wniosków). Wprowadzenie zaproponowanych poprawek może pozytywnie wpłynąć na odbiór aplikacji przez użytkowników końcowych.
