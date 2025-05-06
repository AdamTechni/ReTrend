# ReTrend
### Backend platformy C2C do sprzedaży i wymiany ubrań (inspirowany Vinted)

**Projekt:** ReTrend  
**Opis:** Backend uproszczonej platformy C2C umożliwiającej użytkownikom sprzedaż i wymianę używanej odzieży oraz akcesoriów.  
**Technologie:** Python, FastAPI, SQLAlchemy, PostgreSQL, WebSocket, Docker

---

## 1. Opis projektu

Główne funkcjonalności:
- zarządzanie użytkownikami: rejestracja, logowanie (JWT), edycja profilu
- wystawianie przedmiotów: ogłoszenia z opisem, zdjęciami (URL), ceną, kategorią, rozmiarem, stanem
- przeglądanie: listowanie, filtrowanie, wyszukiwanie
- proces zakupu: tworzenie transakcji, zmiana statusu przedmiotu
- czat (WebSocket): komunikacja w czasie rzeczywistym między użytkownikami
- cel: działający szkielet backendu platformy typu marketplace

---

## 2. Wymagania projektowe

Zrealizowane:
- dokumentacja i API (wersja podstawowa)
- autentykacja użytkowników (JWT)
- domeny: User, Item, Order
- CRUD dla głównych modeli
- komunikacja przez WebSocket
- Dockerfile i opcjonalnie docker-compose.yml

Pominięte lub uproszczone:
- realne płatności
- system dostaw
- upload zdjęć (obsługa tylko URL)
- zaawansowane wyszukiwanie
- system ocen, panel administratora, powiadomienia

---

## 3. Jak korzystać z API

Przykładowy przepływ:
1. Rejestracja: `POST /api/auth/register`
2. Logowanie: `POST /api/auth/login` → JWT
3. Autoryzacja: nagłówek `Authorization: Bearer <token>`
4. Dodanie przedmiotu: `POST /api/items`
5. Przeglądanie: `GET /api/items`
6. Szczegóły: `GET /api/items/{itemId}`
7. Czat:
   - tworzenie: `POST /api/conversations`
   - WebSocket: `ws://localhost:8000/ws/chat/{conversationId}`
8. Zakup: `POST /api/orders`
9. Zamówienia: `GET /api/orders/my-buying`, `GET /api/orders/my-selling`

---

## 4. Kluczowe endpointy (przykłady)

**Autentykacja** (`/api/auth`)
- `POST /register`
- `POST /login`

**Użytkownicy** (`/api/users`)
- `GET /me`
- `PUT /me`
- `GET /{userId}`

**Przedmioty** (`/api/items`)
- `POST /`
- `GET /`
- `GET /{itemId}`
- `PUT /{itemId}`
- `DELETE /{itemId}`

**Zamówienia** (`/api/orders`)
- `POST /`
- `GET /my-buying`
- `GET /my-selling`
- `GET /{orderId}`
- `PUT /{orderId}/status`

**Czat** (`/api/conversations`, `/api/messages`)
- `POST /conversations`
- `GET /conversations/my`
- `GET /conversations/{conversationId}/messages`

**WebSocket** (`/ws`)
- połączenie: `ws://localhost:8000/ws/chat`
- wysyłanie: `/app/chat.sendMessage`
- subskrypcja: `/topic/conversation/{conversationId}`

---

## 5. Technologie

- język: Python
- frameworki: FastAPI, SQLAlchemy, Pydantic, WebSockets
- baza danych: PostgreSQL
- konteneryzacja: Docker, Docker Compose
