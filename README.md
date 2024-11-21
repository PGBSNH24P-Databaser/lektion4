---
author: Lektion 4
date: MMMM dd, YYYY
paging: "%d / %d"
---

# Lektion 4

Hej och välkommen!

## Agenda

1. Frågor, quiz och repetition
2. Avstämning - vad är svårt?
3. Introduktion till relationer
4. Övning med handledning
5. Quiz frågor

---

# Quiz frågor

- Vad är en connection string?
- Varför skall man inte lägga in query-argument genom string concatenation?
- Hur lägger man in argument med en `NpsqlCommand` query?
- Vilka argument tar `NpgsqlCommand` klass-constructorn in?
- Namnge 3 constraints
- Vad heter funktionen för att räkna antal rader?
- Vad är `char_length` för typ av funktion?
- Vad gör `GROUP BY`?
- Är `SERIAL` en constraint?
- Vad gör `UNIQUE`?
- Vad är det för skillnad på `NOT NULL` och `CHECK`?
- Det finns "primary" keys och ??? keys?

---

# Hur sparas listor av saker i SQL-databaser?

En kolumn kan endast spara ett värde. Inte flera som en array. Istället hanteras listor av saker med "relationer".

En relation bildas när en rad i en tabell har en länk till en annan rad, oftast i en annan tabell.

---

# Exempel relation: Människor <-> Husdjur

```md
humans:

| name   | age |
| ------ | --- |
| Bob    | 30  |
| Rachel | 27  |

pets:

| name    | owner  |
| ------- | ------ |
| Charlie | Bob    |
| Oskar   | Bob    |
| Nevad   | Rachel |
```

---

# Primary keys och foreign keys

En relation är en länk mellan två rader. För att skapa en länk så används primary keys och foreign keys.

**Primary key**: en identifierande kolumn. Den är självstående.

**Foreign key**: en refererande kolumn. Refererar till en primary key.

För att referera till en primary key har foreign keys alltid samma värde som en primary key. En primary key kan dock vara helt unik, och utan foreign key.

I exemplet med människor och husdjur så är `humans:name` en primary key och `pets:owner` en foreign key.

---

# Typer av relationer

## One-to-One

En rad refererar till exakt en rad. Förekommer sällan.

Exempel: barn -> pappa, nyckel -> lås

## One-to-Many och Many-to-One

En rad refererar till flera (0-n) rader. One-to-Many och Many-to-One är samma sak från olika perspektiv.

Exempel: människor <-> husdjur, användare <-> kommentarer

## Many-to-Many

Flera rader refererar till flera rader. Om One-to-Many går åt båda hållen så är det Many-to-Many. Skapas med "junction" tabeller.

Exempel: användare <-> git repos, spelare <-> spel

---

# Quiz frågor

- Om man vill spara en lista med saker i PostgreSQL, vad gör man?
- Vad är det för skillnad på en primary key och en foreign key?
- Vad måste finnas för att bilda en relation?
- Alla har en pappa, och endast en pappa. Vad är det för typ av relation i SQL sammanhang?
- Vad är det för skillnad på Many-to-One och One-to-Many relationer?
- Är GitHub repos + users en form av Many-to-Many relation?
- Hur implementeras Many-to-Many relationer med tabeller?
