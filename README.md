# ScanCheck

ScanCheck — это скрипт на языке Python, который анализирует безопасность данного веб-сайта, проверяя его HTTP-заголовки и DNS-записи. Скрипт формирует отчет о безопасности с рекомендациями по устранению потенциальных уязвимостей.
## Функционал:

1. Одинаковые сценарии сайта
2. Записи SPF
3. Записи DMARC
4. Публичная страница администратора
5. Листинг в каталоге
6. Отсутствующие заголовки безопасности
7. Небезопасные настройки файлов cookie
8. Раскрытие информации
9. Неправильные конфигурации совместного использования ресурсов между источниками (CORS)
10. Сниффинг типа содержимого
11. Кэш-контроль


## ScanCheck

- Python 3.6 or higher
- `requests` library
- `beautifulsoup4` library
- `dnspython` library

Эти зависимости можно установить с помощью `pip`:

```
pip install requests beautifulsoup4 dnspython
```

## Запуск

To use the ScanCheck script, follow these steps:

1. Сохраните код в файл с именем `ScanCheck.py`.
2. Открыть терминал и перейти к директории в которой находиться скрипт
3. Дальше запустить с помощью этой команды:

```
python ScanCheck.py
```

4. При появлении запроса введите URL-адрес веб-сайта, который вы хотите проанализировать.
5. Просмотрите созданный отчет о безопасности на наличие потенциальных уязвимостей и рекомендаций.

В отчете о безопасности будет отображаться заголовок или тестовый случай, состояние (Отсутствует, Доступно, Включено и т. д.), серьезность (Низкая, Средняя или Высокая) и рекомендации по устранению проблемы.

## Например

```
Enter the URL to analyze: https://example.com

Security Report:
Header                       Status          Severity   Recommendation
--------------------------------------------------------------------------------
Meta Referrer                Missing         Low        Add a 'referrer' META tag with 'no-referrer' to prevent Same Site Scripting.
SPF Record                   Missing         Low        Add an SPF record to your domain's DNS settings to help prevent email spoofing.
DMARC Record                 Missing         Low        Add a DMARC record to your domain's DNS settings to help protect against email spoofing and phishing.
Public Admin Page            Accessible      High       Restrict access to your admin page to specific IP addresses and/or enable authentication.
Directory Listing            Enabled         Medium     Disable directory listing to prevent unauthorized access to your website's files and folders.
Content-Security-Policy      Missing         Medium     Implement a Content Security Policy (CSP) to prevent Cross-Site Scripting (XSS) and other code injection attacks.
X-Content-Type-Options       Missing         Medium     Set the 'X-Content-Type-Options' header to 'nosniff' to prevent MIME type sniffing.
X-Frame-Options              Missing         Medium     Set the 'X-Frame-Options' header to 'DENY' or 'SAMEORIGIN' to protect against clickjacking.
X-XSS-Protection             Missing         Medium     Set the 'X-XSS-Protection' header to '1; mode=block' to enable XSS protection in older browsers.
Strict-Transport-Security    Missing         Medium     Implement Strict Transport Security (HSTS) to enforce secure connections.
Set-Cookie                   Insecure        High       Set the 'Secure' and 'HttpOnly' flags for cookies to protect them from interception and access by JavaScript.
Server                       Value: nginx    Low        Remove or obfuscate the 'Server' header to avoid revealing server information.
X-Powered-By                 Value: PHP/7.4  Low        Remove or obfuscate the 'X-Powered-By' header to avoid revealing technology stack information.
Access-Control-Allow-Origin  Misconfigured   High       Restrict the 'Access-Control-Allow-Origin' header to specific trusted domains or avoid using the wildcard '*'.
Cache-Control                Insecure        Medium     Set 'Cache-Control' header to 'no-store, private' for sensitive resources to prevent caching.
```

Keep in mind that the script may not cover all possible security scenarios, and it's recommended to perform a thorough security assessment for your website.


