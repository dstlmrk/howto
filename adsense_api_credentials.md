# Jak získat AdSense API credentials

## `account_id`
Parametr ziskate prihlasenim do AdSense,
kde v nastaveni najdete vase id ve tvaru: `pub-0000000000000000`.

## `client_id` a `client_secret`
Pod google uctem je nutne vasemu projektu povolit
na [console.developers.google.com](https://console.developers.google.com/apis/credentials)
zvolene API (v tomto pripade AdSense Management API).
Dale vytvorite OAuth 2.0 credentials pro vasi novou aplikaci.
Vygeneruje se json, kde je id clienta a jeho secret key.

## `refresh_token`
Do prohlizece vlozite nasledujici link, vyberete spravny ucet a vlastni aplikaci date svoleni k cteni AdSense:
```
https://accounts.google.com/o/oauth2/v2/auth?scope=https://www.googleapis.com/auth/adsense.readonly&response_type=code&redirect_uri=http://127.0.0.1:9004&client_id=<client_id>
```

Po potvrzeni posledniho formulare se prohlizec presmeruje a v adresnim radku najdete podobnou adresu:
```
http://127.0.0.1:9004/?code=4/AABH...8HQtHZcQ_lA8#
```

Parametr `code` pouzijete pro prvni prihlaseni, ktere vam vrati `refresh_token`. Prihlaseni provedete POST requestem:
```
POST /oauth2/v4/token HTTP/1.1
Host: www.googleapis.com
Content-Type: application/x-www-form-urlencoded

code=4/AABH...8HQtHZcQ_lA8#
client_id=<client_id>&
client_secret=<client_secret>&
redirect_uri=http://127.0.0.1:9004&
grant_type=authorization_code
```
