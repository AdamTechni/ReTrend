# ReTrend

# ReTrend - Backend aplikacji C2C do sprzedaży i wymiany ubrań

## 1. Czym jest projekt?

**ReTrend** to backend dla uproszczonej platformy C2C inspirowanej Vinted, umożliwiającej użytkownikom sprzedaż i wymianę używanej odzieży oraz akcesoriów.

### Główne funkcjonalności:

- **Zarządzanie użytkownikami**: rejestracja, logowanie (JWT), zarządzanie profilem.
- **Wystawianie przedmiotów**: tworzenie ogłoszeń z opisem, zdjęciami (URL), ceną, kategorią, rozmiarem, stanem.
- **Przeglądanie**: listowanie, filtrowanie, wyszukiwanie.
- **Proces zakupu**: tworzenie transakcji, zmiana statusu przedmiotu.
- **Czat (WebSocket)**: komunikacja w czasie rzeczywistym między użytkownikami.
- **Cel**: działający szkielet backendowy platformy marketplace.

---

## 2. Wymagania projektowe

### Realizowane:

- Dokumentacja i API (wstępna wersja).
- Autentykacja użytkowników (Spring Security + JWT).
- Domeny: `User`, `Item`, `Order`.
- CRUD dla głównych modeli.
- WebSocket do komunikacji.
- Dockerfile + opcjonalnie `docker-compose.yml`.

### Pominięte (lub uproszczone):

- Realne płatności.
- System wysyłki.
- Upload zdjęć (jedynie URL-e).
- Zaawansowane wyszukiwanie.
- System ocen, panel admina, powiadomienia.

---

## 3. Jak korzystać z API?

### Przykładowy przepływ:

1. **Rejestracja:** `POST /api/auth/register`
2. **Logowanie:** `POST /api/auth/login` → JWT
3. **Autoryzacja:** JWT w nagłówku `Authorization: Bearer <token>`
4. **Dodanie przedmiotu:** `POST /api/items`
5. **Przeglądanie:** `GET /api/items`
6. **Szczegóły przedmiotu:** `GET /api/items/{itemId}`
7. **Czat:**
   - `POST /api/conversations`
   - WebSocket: `ws://localhost:8080/ws/chat/{conversationId}`
8. **Zakup:** `POST /api/orders`
9. **Zamówienia:** `GET /api/orders/my-buying`, `GET /api/orders/my-selling`

---

## 4. Dokumentacja techniczna (wybrane endpointy)

### Autentykacja (`/api/auth`)
- `POST /register`
- `POST /login`

### Użytkownicy (`/api/users`)
- `GET /me`
- `PUT /me`
- `GET /{userId}`

### Przedmioty (`/api/items`)
- `POST /`
- `GET /`
- `GET /{itemId}`
- `PUT /{itemId}`
- `DELETE /{itemId}`

### Zamówienia (`/api/orders`)
- `POST /`
- `GET /my-buying`
- `GET /my-selling`
- `GET /{orderId}`
- `PUT /{orderId}/status`

### Czat (`/api/conversations`, `/api/messages`)
- `POST /conversations`
- `GET /conversations/my`
- `GET /conversations/{conversationId}/messages`

### WebSocket (`/ws`)
- `ws://localhost:8080/ws/chat`
- Wysyłanie: `/app/chat.sendMessage`
- Subskrypcja: `/topic/conversation/{conversationId}`

---

## Technologie:

- **Język**: Java
- **Frameworki**: Spring Boot, Spring Security, Spring Data JPA, Spring WebSocket
- **Baza danych**: PostgreSQL
- **Konteneryzacja**: Docker

---

## Autorzy i licencja

Projekt stworzony do celów edukacyjnych lub jako szkielet komercyjny. Licencja i autorzy zostaną określeni w wersji końcowej.
