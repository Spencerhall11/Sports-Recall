# Sports-Recall
OCaml tool to pull a team roster and season records from TheSportsDB with a name input, has local SQLite Caching
Built as a first OCaml project to develop familiarity with the language's type system, module architecture, and async IO — part of a broader polyglot systems portfolio.

## Features

- Team lookup by name
- Full roster display with position, nationality, and date of birth
- Season records for up to four seasons including rank, wins, losses, draws, and points
- Graceful handling of missing or empty API responses
- Modular architecture separating API, parsing, display, and types

## Stack

- **OCaml 5.5.0**
- **Dune** — build system
- **Cohttp + Lwt** — async HTTP client
- **Yojson** — JSON parsing
- **SQLite3** — local cache (scaffolded)
- **TheSportsDB** — free sports data API, no key required for basic queries

## Build

Requires [opam](https://opam.ocaml.org/) and OCaml 5.x.

```bash
opam install dune cohttp-lwt-unix yojson sqlite3 lwt lwt.unix lwt_ssl
dune build
```

## Run

```bash
dune exec bin/main.exe
```

Enter a team name and it will then search the team. Works best with English Premier League teams.


## Project Structure
lib/

types.ml    — shared record types

parser.ml   — JSON to typed record conversion

api.ml      — async HTTP calls to TheSportsDB

cache.ml    — SQLite caching layer

display.ml  — terminal output formatting

bin/

main.ml     — entry point 


## Example output
=== Liverpool ===
League: English Premier League

--- Roster ---
Alexander Isak            Centre-Forward  Sweden               1999-09-21
Alexis Mac Allister       Central Midfield Argentina            1998-12-24
Alisson Becker            Goalkeeper      Brazil               1992-10-02
Andoni Iraola             Manager         Spain                1982-06-22
Ármin Pécsi             Goalkeeper      Hungary              2005-02-24
Cody Gakpo                Left Wing       The Netherlands      1999-05-07
Conor Bradley             Right-Back      Northern Ireland     2003-07-09
Curtis Jones              Central Midfield England              2001-01-30
Dominik Szoboszlai        Central Midfield Hungary              2000-10-25
Federico Chiesa           Left Wing       Italy                1997-10-25

--- Season Records ---
Season       Rank   W      L      D      Pts   
2023-2024    3      24     4      10     82    
2022-2023    5      19     9      10     67    
2021-2022    2      28     2      8      92    
2020-2021    3      20     9      9      69   



## Notes

- TheSportsDB free tier does not include all teams or all seasons
- Roster results may be paginated by the API
- Cache layer is scaffolded for future use
EOF



known issues:
Paris Saint Germaine is not available for recall
