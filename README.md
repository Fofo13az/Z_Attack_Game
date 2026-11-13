# Z_Attack

> **About this fork**: This is my fork of the team repository ([NovaPhi/Game](https://github.com/NovaPhi/Game)), kept for my portfolio. Z Attack is a web-based roguelite card game built by a team of 3 at Tec de Monterrey (Feb–May 2026): HTML/CSS/JS frontend, Node.js/Express REST API, and a MariaDB database, all run with Docker Compose.
>
> ### My contributions (Adolfo Hernández Sánchez)
> - **Card collection & deck builder**: the frontend for browsing cards and building decks, plus a first version of the card-unlock system ([`cards.js`](Z_Attack/JS/cards.js), [`DeckBuilder.js`](Z_Attack/JS/DeckBuilder.js), [`cardsUnlock.js`](Z_Attack/JS/cardsUnlock.js)).
> - **Admin analytics dashboard**: REST endpoints and Chart.js charts of player and run data, plus admin views of users and connection logs ([`Admin.js`](Z_Attack/Api/Admin.js), [`dataGraph.js`](Z_Attack/Api/dataGraph.js), [`AdminPage.html`](Z_Attack/HTML/AdminPage.html)).
> - **Database:**
>   - Normalized the schema to 3NF, from 9 to 13 tables, with the ER diagram and the justification document.
>   - Added a connection-log table with an index for its queries.
>   - Extended `saveStats` so it records every run.
>   - Fixed seed data that referenced heroes and cards that didn't exist.
> - **Game world:** map obstacles and barriers, and the integration of the backgrounds and sprites, including a style guide for AI-assisted asset generation.
> - **Documentation:** the JS, API endpoint, admin page, and CSS docs.

---

A web-based card game with a Node.js backend and MariaDB database. Run the full stack locally with Docker no need to install Node.js or MariaDB.

---

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Git](https://git-scm.com)

---

## Setup

### Step 1 - Clone the repo
```bash
git clone https://github.com/NovaPhi/Game.git
cd Game
```

### Step 2 - Create your `.env` file
```bash
cp .env.example .env
```
Open `.env` and set your passwords:
```env
DB_NAME=Z_ATTACK
DB_USER=zattack_user
DB_PASSWORD=yourpassword
DB_ROOT_PASSWORD=yourrootpassword
API_PORT=8081
FRONTEND_PORT=3000
```

### Step 3 - Start Docker
```bash
docker compose up --build
```

### Step 4 - Open the game
```
http://localhost:3000/Z_Attack/HTML/main.html
```

---

## Useful Commands

```bash
docker compose down          # stop everything
docker compose down -v       # stop + wipe database (full reset)
docker compose logs -f       # live logs from all containers
docker compose logs -f api   # API logs only
docker compose logs -f db    # DB logs only
```

---

## Troubleshooting Suggestions

**Data empty after signup**
The `init/02-cards.sql` file may not have loaded. Run a full reset:
```bash
docker compose down -v
docker compose up --build
```

**API says "DB connection failed"**
The database might still be importing. Wait 30 seconds then:
```bash
docker compose restart api
```

**Port already in use**
Change `API_PORT` or `FRONTEND_PORT` in your `.env` file and restart.

---

## Accesibility

For accesibility we made a setting where the user if colorblind can choose the colorscheme change depending on the type of colorblindness they have this is because colorblindess is one of the most common issues affecting gamers in the world we felt that this setting would be impactfull to the most people.

***Md notation done with the help of claude
