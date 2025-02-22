# PostgreSQL Installation auf Arch Linux

## 1. System aktualisieren

Bevor du PostgreSQL installierst, solltest du dein System auf den neuesten Stand bringen:

```sh
sudo pacman -Syu
```

---

## 2. PostgreSQL installieren

Installiere den PostgreSQL-Server und -Client mit:

```sh
sudo pacman -S postgresql
```

---

## 3. Datenbank-Cluster initialisieren

Bevor du PostgreSQL verwenden kannst, musst du den **Datenbank-Cluster** einrichten:

```sh
sudo -iu postgres
initdb --locale $LANG -E UTF8 -D '/var/lib/postgres/data'
```

🔹 **Erklärung der Parameter:**

- `--locale $LANG` → Setzt die Spracheinstellungen für die DB.
- `-E UTF8` → Nutzt UTF-8 als Zeichenkodierung.
- `-D '/var/lib/postgres/data'` → Speichert die Datenbank unter diesem Pfad.

---

## 4. PostgreSQL-Dienst starten & aktivieren

Starte PostgreSQL und stelle sicher, dass es beim Systemstart automatisch geladen wird:

```sh
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

---

## 5. PostgreSQL-Benutzer erstellen

Wechsle zum **PostgreSQL-User**:

```sh
sudo -iu postgres
```

Erstelle dann einen neuen Benutzer interaktiv:

```sh
createuser --interactive
```

👉 Du wirst gefragt, welchen Namen der Benutzer haben soll und ob er ein **Superuser** sein soll.

---

## 6. Neue Datenbank erstellen

Nachdem dein Benutzer eingerichtet ist, kannst du eine neue Datenbank anlegen:

```sh
createdb your-database-name
```

---

## 7. PostgreSQL-Shell betreten

Um mit der Datenbank zu arbeiten, starte die PostgreSQL-CLI:

```sh
psql
```

Oder verbinde dich direkt zu einer bestimmten Datenbank:

```sh
psql your-database-name
```

---

## 8. PostgreSQL-Shell verlassen

Wenn du fertig bist, kannst du die Shell mit folgendem Befehl verlassen:

```sh
\q
```

---

✨ **Fertig!** Deine PostgreSQL-Datenbank ist nun bereit zur Nutzung. 🚀  
Falls du **Remote-Zugriff** oder **Benutzerrechte** anpassen möchtest, kannst du die `pg_hba.conf` und `postgresql.conf` bearbeiten.

## 9. Find dbs

```sh
sudo -iu postgres psql -c "\l"
```

---

## 10. Use db

```sh
DATABASE_URL="postgresql://postgres:deinPasswort@localhost:5432/db_name"
```

---
