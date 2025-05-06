# ReTrend
# Backend platformy C2C do sprzedaży i wymiany ubrań (inspirowany Vinted)

"""
Projekt: ReTrend
Opis: Backend uproszczonej platformy C2C umożliwiającej użytkownikom sprzedaż i wymianę używanej odzieży oraz akcesoriów.
Technologie: Python, FastAPI, SQLAlchemy, PostgreSQL, WebSocket, Docker
"""

# ------------------------------
# 1. Opis projektu
# ------------------------------

# Główne funkcjonalności:
# - Zarządzanie użytkownikami: rejestracja, logowanie (JWT), edycja profilu
# - Wystawianie przedmiotów: ogłoszenia z opisem, zdjęciami (URL), ceną, kategorią, rozmiarem, stanem
# - Przeglądanie: listowanie, filtrowanie, wyszukiwanie
# - Proces zakupu: tworzenie transakcji, zmiana statusu przedmiotu
# - Czat (WebSocket): komunikacja w czasie rzeczywistym między użytkownikami
# - Cel: działający szkielet backendu platformy typu marketplace

# ------------------------------
# 2. Wymagania projektowe
# ------------------------------

# Zrealizowane:
# - Dokumentacja i API (wersja podstawowa)
# - Autentykacja użytkowników (JWT)
# - Domeny: User, Item, Order
# - CRUD dla głównych modeli
# - Komunikacja przez WebSocket
# - Dockerfile i opcjonalnie docker-compose.yml

# Pominięte lub uproszczone:
# - Realne płatności
# - System dostaw
# - Upload zdjęć (obsługa tylko URL)
# - Zaawansowane wyszukiwanie
# - System ocen, panel administratora, powiadomienia

# ------------------------------
# 3. Jak korzystać z API
# ------------------------------

# Przykładowy przepływ:
# 1. Rejestracja:        POST /api/auth/register
# 2. Logowanie:          POST /api/auth/login  → JWT
# 3. Autoryzacja:        Nagłówek "Authorization: Bearer <token>"
# 4. Dodanie przedmiotu: POST /api/items
# 5. Przeglądanie:       GET /api/items
# 6. Szczegóły:          GET /api/items/{itemId}
# 7. Czat:
#    - Tworzenie:        POST /api/conversations
#    - WebSocket:        ws://localhost:8000/ws/chat/{conversationId}
# 8. Zakup:              POST /api/orders
# 9. Zamówienia:         GET /api/orders/my-buying, /my-selling

# ------------------------------
# 4. Kluczowe endpointy (przykłady)
# ------------------------------

# AUTENTYKACJA (/api/auth)
# - POST /register
# - POST /login

# UŻYTKOWNICY (/api/users)
# - GET /me
# - PUT /me
# - GET /{userId}

# PRZEDMIOTY (/api/items)
# - POST /
# - GET /
# - GET /{itemId}
# - PUT /{itemId}
# - DELETE /{itemId}

# ZAMÓWIENIA (/api/orders)
# - POST /
# - GET /my-buying
# - GET /my-selling
# - GET /{orderId}
# - PUT /{orderId}/status

# CZAT (/api/conversations, /api/messages)
# - POST /conversations
# - GET /conversations/my
# - GET /conversations/{conversationId}/messages

# WEBSOCKET (/ws)
# - ws://localhost:8000/ws/chat
# - Wysyłanie: /app/chat.sendMessage
# - Subskrypcja: /topic/conversation/{conversationId}

# ------------------------------
# 5. Technologie
# ------------------------------

# - Język: Python
# - Frameworki: FastAPI, SQLAlchemy, Pydantic, WebSockets
# - Baza danych: PostgreSQL
# - Konteneryzacja: Docker, Docker Compose
