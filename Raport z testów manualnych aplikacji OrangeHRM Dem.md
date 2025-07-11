# Raport z testów manualnych aplikacji OrangeHRM Demo

## 1. Wstęp

Testy zostały przeprowadzone na demo aplikacji HR dostępnej pod adresem: https://opensource-demo.orangehrmlive.com/. Użyto konta testowego:  
Login: **Admin**  
Hasło: **admin123**

Wybrane funkcjonalności do testów:
- Zarządzanie pracownikami (PIM – Personal Information Management)
- Urlopy (Leave)

## 2. Przebieg testów

### 2.1. Funkcjonalność: Zarządzanie pracownikami (PIM)

**Zakres testów:**
- Dodawanie nowego pracownika
- Wyszukiwanie pracownika
- Edycja danych pracownika

**Kroki testowe:**
1. Przejście do modułu PIM.
2. Wybranie opcji „Add Employee”.
3. Wprowadzenie danych (imię, nazwisko, zdjęcie).
4. Zapisanie nowego pracownika.
5. Wyszukanie utworzonego pracownika po imieniu/nazwisku.
6. Edycja danych pracownika.
7. Zapisanie zmian.

**Wyniki:**
- Dodanie i wyszukiwanie pracownika przebiegło pomyślnie.
- Edycja danych działa poprawnie, zmiany są widoczne po zapisaniu.

**Znalezione błędy:**
- Brak walidacji formatu zdjęcia – możliwe jest przesłanie pliku o niepoprawnym formacie.
- Po zapisaniu nowego pracownika nie pojawia się jednoznaczne potwierdzenie sukcesu (brak komunikatu).

**Propozycje usprawnień:**
- Dodanie komunikatu potwierdzającego dodanie/edycję pracownika.
- Ulepszenie walidacji pól formularza (np. ograniczenie długości pól, walidacja zdjęcia).
- Dodanie możliwości cofnięcia zmian przed zapisaniem.

### 2.2. Funkcjonalność: Urlopy (Leave)

**Zakres testów:**
- Składanie wniosku urlopowego
- Przeglądanie historii urlopów
- Akceptacja/odrzucanie wniosków

**Kroki testowe:**
1. Przejście do modułu „Leave”.
2. Wybranie opcji „Apply”.
3. Wypełnienie wniosku urlopowego (typ urlopu, daty, komentarz).
4. Złożenie wniosku.
5. Przejście do „My Leave” – sprawdzenie, czy wniosek się pojawił.
6. Przejście do „Leave List” – sprawdzenie możliwości filtrowania i przeglądania wniosków.

**Wyniki:**
- Wniosek urlopowy został złożony i pojawił się na liście.
- Filtrowanie działa poprawnie.
- Statusy są czytelne.

**Znalezione błędy:**
- Brak walidacji dat – możliwe jest złożenie wniosku na daty wsteczne.
- Po złożeniu wniosku nie pojawia się natychmiastowy komunikat potwierdzający.

**Propozycje usprawnień:**
- Dodanie walidacji dat (blokada wyboru dat przeszłych).
- Dodanie powiadomienia o sukcesie po złożeniu wniosku.
- Umożliwienie edycji lub anulowania wniosku przed rozpatrzeniem.

## 3. Podsumowanie

Aplikacja OrangeHRM Demo oferuje szeroki zakres funkcjonalności HR. Podczas testów wybrane moduły działały stabilnie, jednak zauważono kilka błędów i obszarów do usprawnienia, szczególnie w zakresie walidacji formularzy oraz komunikacji z użytkownikiem (brak jasnych komunikatów potwierdzających operacje).

## 4. Tabela błędów i usprawnień

| Funkcjonalność | Błąd/Usprawnienie                | Opis                                                                 |
|----------------|----------------------------------|----------------------------------------------------------------------|
| PIM            | Brak walidacji zdjęcia           | Możliwość przesłania pliku o nieprawidłowym formacie                 |
| PIM            | Brak komunikatu sukcesu          | Po dodaniu/edycji brak potwierdzenia dla użytkownika                 |
| Leave          | Brak walidacji dat               | Możliwość złożenia wniosku na daty wsteczne                          |
| Leave          | Brak komunikatu po złożeniu      | Po złożeniu wniosku brak potwierdzenia na ekranie                    |
| Leave          | Brak możliwości edycji wniosku   | Użytkownik nie może edytować/anulować wniosku przed rozpatrzeniem    |

## 5. Wnioski

Rekomenduję wdrożenie powyższych usprawnień, co poprawi użyteczność, bezpieczeństwo oraz komfort pracy użytkowników systemu.
