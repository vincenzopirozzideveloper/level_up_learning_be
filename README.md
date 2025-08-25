# Level Up Learning - Backend

Backend API per Level Up Learning sviluppato con Laravel e Sanctum per l'autenticazione.

## Requisiti

- PHP 8.1+
- Composer
- MariaDB/MySQL
- Docker (opzionale)

## Installazione

1. Clona il repository:
```bash
git clone git@github.com:vincenzopirozzideveloper/level_up_learning_be.git
cd level_up_learning_be
```

2. Installa le dipendenze:
```bash
composer install
```

3. Copia il file di configurazione:
```bash
cp .env.example .env
```

4. Genera la chiave dell'applicazione:
```bash
php artisan key:generate
```

5. Configura il database nel file `.env`:
```env
DB_CONNECTION=mysql
DB_HOST=172.20.0.5
DB_PORT=3306
DB_DATABASE=levelup_db
DB_USERNAME=levelup_user
DB_PASSWORD=levelup_password
```

6. Esegui le migrazioni:
```bash
php artisan migrate
```

## API Endpoints

### Autenticazione

- `POST /api/register` - Registrazione nuovo utente
- `POST /api/login` - Login utente
- `POST /api/logout` - Logout (richiede autenticazione)
- `GET /api/user` - Ottieni utente corrente (richiede autenticazione)

### Utilizzo con Frontend React

Il backend è configurato per funzionare con un frontend React su `localhost:3000`.

Prima di fare richieste di login, ottieni il CSRF token:
```javascript
await axios.get('http://localhost/sanctum/csrf-cookie');
```

Poi puoi effettuare il login:
```javascript
await axios.post('http://localhost/api/login', {
    email: 'user@example.com',
    password: 'password'
}, {
    withCredentials: true
});
```

## Configurazione CORS

Il CORS è configurato per accettare richieste da:
- `http://localhost`
- `http://localhost:3000`

Modifica `config/cors.php` per aggiungere altri domini.

## Docker

Il progetto è configurato per funzionare con Docker. Il database MariaDB è configurato con:
- Container: `levelup_learn_mariadb`
- Network: `LevelUp_Network`
- IP: `172.20.0.5`

## Licenza

Proprietario