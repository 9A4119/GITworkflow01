# GITworkflow01
WORKING FROM GITBASH 2 push into github01
sample restaurantAPP
version: '3.7'

services:
  frontend:
    build:
      context: ./frontend
    ports:
      - "8000:8000"
    depends_on:
      - backend

  backend:
    build:
      context: ./backend
    ports:
      - "5000:5000"
    environment:
      - DATABASE_URL=postgres://username:password@db:5432/restaurant_db
    volumes:
      - backend-data:/app/data
Restart always:
  db:
    image: postgres:latest
    environment:
      POSTGRES_DB: restaurant_db
      POSTGRES_USER: username
      POSTGRES_PASSWORD: password
    ports:
      - "5432:5432"
    volumes:
      - db-data:/var/lib/postgresql/data
Restart always:

volumes:
  backend-data:
  db-data:

