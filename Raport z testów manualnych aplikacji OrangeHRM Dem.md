# Raport z testów manualnych aplikacji OrangeHRM Demo

## Wstęp

Celem testów było sprawdzenie wybranych funkcjonalności demo systemu HR dostępnego pod adresem https://opensource-demo.orangehrmlive.com/. Testy przeprowadzono po zalogowaniu się na konto Admin (login: Admin, hasło: admin123). Wybrano dwie funkcjonalności:

- Zarządzanie użytkownikami (Admin → User Management → Users)
- Moduł urlopów (Leave)

Poniżej znajduje się szczegółowy opis przeprowadzonych testów, wykryte błędy oraz propozycje usprawnień.

## Funkcjonalność 1: Zarządzanie użytkownikami

### Kroki testowe

#### 1. Wyświetlanie listy użytkowników
1. Zaloguj się do aplikacji:  
   - Adres: https://opensource-demo.orangehrmlive.com/  
   - Login: `Admin`  
   - Hasło: `admin123`
2. Po zalogowaniu kliknij w menu po lewej stronie na **Admin**.
3. W podmenu wybierz **User Management** → **Users**.
4. Sprawdź, czy lista użytkowników jest wyświetlana poprawnie.

#### 2. Filtrowanie i wyszukiwanie użytkowników
1. W sekcji **System Users** użyj pola **User Role** – wybierz dowolną rolę z listy (np. `ESS`).
2. Kliknij **Search**.
3. Sprawdź, czy lista użytkowników została przefiltrowana zgodnie z wybraną rolą.
4. W polu **Username** wpisz fragment nazwy istniejącego użytkownika.
5. Kliknij **Search**.
6. Sprawdź, czy wyniki odpowiadają wpisanej frazie.

#### 3. Dodawanie nowego użytkownika
1. Kliknij przycisk **Add** nad listą użytkowników.
2. Wypełnij formularz:
   - User Role: np. `ESS`
   - Employee Name: wpisz np. `Linda Anderson` (wybierz z podpowiedzi)
   - Status: `Enabled`
   - Username: np. `testuser123`
   - Password: np. `Test@1234`
   - Confirm Password: `Test@1234`
3. Kliknij **Save**.
4. Sprawdź, czy pojawia się komunikat o sukcesie oraz czy nowy użytkownik pojawia się na liście.

#### 4. Edycja istniejącego użytkownika
1. Na liście użytkowników znajdź użytkownika (np. `testuser123`).
2. Kliknij ikonę **Edit** (ołówek) przy tym użytkowniku.
3. Zmień np. status na `Disabled`.
4. Kliknij **Save**.
5. Sprawdź, czy zmiana została zapisana.

#### 5. Usuwanie użytkownika
1. Na liście użytkowników zaznacz pole przy wybranym użytkowniku (np. `testuser123`).
2. Kliknij przycisk **Delete** (ikona kosza).
3. Potwierdź usunięcie w oknie dialogowym.
4. Sprawdź, czy użytkownik został usunięty z listy.

## Funkcjonalność 2: Moduł urlopów (Leave)

### Kroki testowe

#### 1. Składanie wniosku urlopowego
1. W menu po lewej stronie kliknij **Leave**.
2. Wybierz **Apply**.
3. W formularzu wybierz:
   - Leave Type: np. `CAN - Bereavement`
   - From Date: wybierz datę (np. dzisiejszą)
   - To Date: wybierz tę samą datę
   - Comment: wpisz np. `Testowy wniosek urlopowy`
4. Kliknij **Apply**.
5. Sprawdź, czy pojawia się komunikat o sukcesie.

#### 2. Przeglądanie historii wniosków
1. W menu **Leave** wybierz **My Leave**.
2. Sprawdź, czy złożony wniosek jest widoczny na liście.
3. Sprawdź szczegóły wniosku, klikając na niego.

#### 3. Akceptacja/odrzucenie wniosku (rola Admin)
1. W menu **Leave** wybierz **Leave List**.
2. Ustaw zakres dat, aby widzieć złożony wcześniej wniosek.
3. Kliknij **Search**.
4. Na liście znajdź wniosek testowy.
5. Kliknij na niego, wybierz **Approve** lub **Reject**.
6. Sprawdź, czy status wniosku zmienił się odpowiednio.

#### 4. Filtrowanie wniosków
1. W menu **Leave** → **Leave List** użyj filtrów:
   - Status (np. `Pending Approval`)
   - Leave Type
   - Employee Name
2. Kliknij **Search**.
3. Sprawdź, czy wyniki odpowiadają zastosowanym filtrom.

## Wyniki testów i błędy

### Zarządzanie użytkownikami

- **Dodawanie użytkownika:** Po dodaniu użytkownika nie zawsze pojawia się komunikat o sukcesie, czasem lista nie odświeża się automatycznie.
- **Filtrowanie:** Działa poprawnie.
- **Edycja:** Działa poprawnie.
- **Usuwanie:** Działa poprawnie.

### Moduł urlopów

- **Składanie wniosku:** Działa poprawnie.
- **Historia:** Działa poprawnie.
- **Akceptacja/odrzucenie:** Status na liście nie zawsze aktualizuje się automatycznie po akcji.
- **Filtrowanie:** Nie można filtrować po kilku statusach jednocześnie.

## Propozycje usprawnień

- Automatyczne odświeżanie list po dodaniu/edycji/usunięciu użytkownika lub zmianie statusu wniosku.
- Wyraźniejsze komunikaty o sukcesie lub błędzie.
- Możliwość filtrowania po wielu statusach jednocześnie w module urlopów.
- Umożliwienie sortowania listy użytkowników po kolumnach.
- Lepsze wyróżnienie statusów kolorami.

## Podsumowanie

Testy wykazały, że aplikacja jest intuicyjna i większość podstawowych funkcji działa poprawnie. Wskazane błędy dotyczą głównie braku automatycznego odświeżania danych oraz niejednoznacznych komunikatów po operacjach. Propozycje usprawnień dotyczą zarówno warstwy funkcjonalnej, jak i UI/UX, co może pozytywnie wpłynąć na komfort użytkowania aplikacji.
