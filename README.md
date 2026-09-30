# Labenu System API

A REST API for managing a coding school: classes (*turmas*), students (*estudantes*) and teachers (*docentes*), with hobbies, specialities and a few search endpoints.

Built in September 2022 during the [Labenu](https://www.labenu.com.br/) full-stack web development bootcamp (module 5, back-end). The domain language is Portuguese, as in the original assignment. The code is kept as it was delivered; only this README was added later.

## Stack

Node.js · TypeScript · Express · MySQL via Knex · uuid

The code is object-oriented: a `Usuario` base class extended by `Estudante` and `Docente`, and one class per database table (`src/classes/`).

## Endpoints

| Method | Path | What it does |
|---|---|---|
| GET | `/turmas` | List all classes |
| GET | `/turmas/:search` | Search classes |
| GET | `/turmas/:id/todos` | Everyone (students and teachers) in a class |
| POST | `/turmas` | Create a class |
| PATCH | `/turma/:id/modulo/:modulo` | Move a class to another module |
| POST | `/estudante` | Create a student (with hobbies) |
| GET | `/estudante/:search` | Search students |
| PATCH | `/estudante/:id/turma/:turmaID` | Move a student to another class |
| GET | `/estudante/hobby/:id` | Students who share a hobby with the given student |
| POST | `/docente` | Create a teacher (with specialities) |
| GET | `/docente` | List teachers |
| GET | `/docente/:especialidade` | Teachers with a given speciality |
| PUT | `/docente/:docenteID/turma/:turmaID` | Assign a teacher to a class |
| GET | `/search/sign/:sign` | Students and teachers by zodiac sign, computed from their birth date (the bootcamp's bonus challenge) |

## Database

MySQL tables used: `turma`, `estudante`, `docente`, `hobbie`, `personal_hobbie`, `personal_especialidade`. The schema script was not part of this folder; the table shapes can be read from the classes in `src/classes/`.

## Run it locally

Create a `.env` in the project root:

```
DB_HOST=
DB_USER=
DB_PASSWORD=
DB_SCHEMA=
```

Then:

```bash
npm install
npm run dev
```

## Known limitations

Left as delivered, bootcamp-era code:

- No schema/migration script and no automated tests.
- Not deployed.
