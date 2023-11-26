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
