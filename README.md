# REST API
Implementace základního REST API pomocí frameworku Express. API obsahuje následující endpointy:

## POST /login
Endpoint pro ověření uživatelů a přihlášení.

### Request
* Metoda: POST
* URL: /login
* Body:
  * username: Uživatelské jméno
  * password: Heslo
### Response
* Úspěch (200 OK): Přihlášení úspěšné, vrátí ID uživatele.
* Chyba (400 Bad Request):
  * Invalid username: Neplatné uživatelské jméno.
  * Invalid password: Neplatné heslo.
## POST /register
Endpoint pro registraci nových uživatelů.

### Request
* Metoda: POST
* URL: /register
* Body:
  * username: Uživatelské jméno
  * email: E-mailová adresa
  * password: Heslo
### Response
* Úspěch (200 OK): Registrace úspěšná.
* Chyba (400 Bad Request):
  * Some parameters are missing: Některé parametry chybějí.
  * Something went wrong: Něco se pokazilo při registraci.
## DELETE /logout
Endpoint pro odhlášení uživatele.

### Request
* Metoda: DELETE
* URL: /logout
### Response
* Úspěch (200 OK): Odhlášení úspěšné.
* Chyba (400 Bad Request): Unable to log out: Chyba při odhlášení.

# /etc/nginx/sites-available
Pro funkční přesměrování z portu 5000 bylo potřeba upravit soubor default v /etc/nginx/sites-available následovně:

    server {
        listen 80 default_server;
        listen [::]:80 default_server;
        servername ;

    location / {
        proxy_pass http://localhost:5000/;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
        try_files $uri @nodejs;
    }

    location @nodejs {
        proxy_pass http://localhost:5000/;
    }
