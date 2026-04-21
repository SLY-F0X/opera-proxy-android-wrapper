# Opera Proxy для Android

Лавочка щедрости серверов Opera на данный момент закрылась. Сарафанный каскад сделал свое дело.
---


Неофициальный Android-клиент и графическая оболочка (Wrapper) для утилиты **[opera-proxy](https://github.com/Snawoot/)** от Snawoot.

---

**Внимание: участились случаи плагиата и распространения вредоносных модификаций**

Ресурс, именующий себя «Киберпортал» (TG), незаконно присвоил исходный код проекта.
Вопреки принципам открытого ПО, авторы клона полностью удалили упоминания об оригинальном авторстве, выдавая чужой труд за собственную разработку под названием **PortalConnect**.

Будьте бдительны: подобные «клоны» могут содержать скрытые угрозы и создаются исключительно с целью монетизации и паразитирования на чужом труде. 

**Оригинальное приложение распространяется бесплатно и только на данном ресурсе [https://github.com/SLY-F0X/opera-proxy-android-wrapper](https://github.com/SLY-F0X/opera-proxy-android-wrapper).
Приложение не представлено на других площадках или в сторонних группах.**

---

<p align="center">
  <a href="https://github.com/SLY-F0X/opera-proxy-android-wrapper/releases/latest"><img alt="Latest_release" src="https://img.shields.io/github/v/release/SLY-F0X/opera-proxy-android-wrapper?display_name=tag&sort=semver&style=for-the-badge"></a>
  <a href="https://github.com/SLY-F0X/opera-proxy-android-wrapper/releases"><img alt="Downloads" src="https://img.shields.io/github/downloads/SLY-F0X/opera-proxy-android-wrapper/total?style=for-the-badge"></a>
</p>

<p align="center">
  <img alt="Android" src="https://img.shields.io/badge/Android-5.0%2B-3DDC84?style=for-the-badge&logo=android&logoColor=white">
  <img alt="ABI" src="https://img.shields.io/badge/ABI-arm64--v8a%20%7C%20armeabi--v7a-informational?style=for-the-badge">
  <img alt="Traffic" src="https://img.shields.io/badge/Traffic-TCP%20only-critical?style=for-the-badge">
</p>


Приложение позволяет использовать инфраструктуру Opera VPN как локальный VPN или локальный прокси на Android-устройстве без необходимости установки браузера Opera.
Весь трафик (или трафик выбранных приложений) маршрутизируется через серверы Opera.
**Приложение создано для максимально простого запуска одной кнопкой.**
Вам не потребуются командная строка (Shell), эмуляторы терминала вроде Termux или сложные конфигурации.

*Не знаете какой APK загрузить?* - *Ответ `universal`*


## ✨ Возможности
*   **НЕ ЯВЛЯЕТСЯ VPN!** **Оболочка VPN нужна для ВЫБОРОЧНОГО проксирования приложений без ROOT прав!**
*   **Не является средством против "белых списков", кому как повезет.**
*   **Реализованы подсказки по функциям в UI, `что бы получить подсказку по свичам удерживайте палец!`**
*   **Работа без Root:** Использует системный API `VpnService` для перехвата трафика. **Больше НЕ использует агрессивные методы загрузки компонентов, по типу `dlopen RTLD_NOW`**
*   **Выбор региона:** Быстрое переключение между серверами Европы (EU), Азии (AS) и Америки (AM).
*   **Раздельное туннелирование (Split Tunneling):** Возможность выбрать конкретные приложения, которые будут работать через прокси, оставляя остальные в прямой сети.
*   **Режим "Только Прокси" (Proxy Only):** Запуск локального сервера (HTTP/SOCKS5) без создания локального VPN-туннеля. Вам необходимо вручную зайти в настройки Wi-Fi и задать IP:PORT для локального прокси. Попробуйте `0.0.0.0:8080`.
*   **Живые логи:** Встроенная консоль для просмотра логов соединения и отладки в реальном времени.
*   **Только TCP:** Поддерживается **только TCP-трафик**. **`Протокол UDP не поддерживается самими серверами Opera.`** Это означает, что голосовые звонки в мессенджерах, онлайн-игры, использующие UDP, и протокол QUIC/HTTP3 через этот прокси работать не будут.
*   **Плитка для запуска в шторке:** Вы можете настроить плитку для быстрого запуска и остановки приложения. Плитка не доступна для Android 6 и ниже.
*   **Ярлыки ЗАПУСКА и ОСТАНОВКИ оболочки VPN при удерживании пальца на ярлыке.**
*   **Применяется агрессивный запрос напрямую разрешения (не через intent) для работы в фоне `android.permission.FOREGROUND_SERVICE`, `FOREGROUND_SERVICE_DATA_SYNC`, `WAKE_LOCK`. А так же запрос прав на отключения оптимизации батареи `REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`.**  `QUERY_ALL_PACKAGES` главный триггер всех ОПАСНЫХ сигнатур, используется для фильтрации приложений в ЛОКАЛЬНОМ VPN. Запрещен для использования в приложениях на Google Play без обоснования зачем вам оно это надо. Вручную же вписывать базовые названия пакетов веселее, не так ли? Чем выбирать из списка в UI ВСЕ пакеты, даже системные :)
*   **Отображение скорости работы туннеля в КБ/с**
*   **Запрос прав на оптимизацию батареи и VPN главном экране через меню в правом углу**
*   **Больше DNS серверов, зачем ограничиваться 1 или 3...**
*   **Данный мануал теперь всегда с вами...**


## 🚀 Расширенные настройки

Для опытных пользователей предусмотрен режим **Advanced Settings**, позволяющий тонко настроить работу прокси:

*   **Proxy Only Mode:** Если включено, VPN-сервис не запускается. Поднимается только локальный прокси-сервер на указанном адресе.
*   **Bind Address:** Настройка локального интерфейса и порта (по умолчанию `127.0.0.1:1080`). Настройки порта работают всегда (VPN/PROXY)
*   **SOCKS Mode:** Переключение протокола локального порта с HTTP на SOCKS5.[SOCKS5 без UDP ASSOCIATE](https://datatracker.ietf.org/doc/html/rfc1928)
*   **Fake SNI:** Подмена SNI (Server Name Indication) при TLS рукопожатии для обхода DPI блокировок. Поле можно заполнить названием сайта, который у вас открывается во время блокировок, без `http / https / www`. Подробнее можете почитать в [Server Name Identification (SNI) Encryption in TLS](https://datatracker.ietf.org/doc/html/rfc8744).
*   **Upstream Proxy:** Возможность пустить трафик Opera Proxy через другой прокси (Chain Proxy). Поддерживаются схемы `socks5://`, `http://`. Например через [ByeByeDPI](https://github.com/romanvht/ByeByeDPI) запуская программу так же в режиме Proxy, с ДРУГИМ портом, отличающимся от  Wrapper. Чаще всего приложения общаются через SOCKS5, потому адресс будет примерно вида `socks5://127.0.0.1:1080`. Можете применять любую другую дурилку, работающую в режиме Proxy.
*   **Bootstrap DNS:** Список DoH/DoT резолверов для начального соединения с серверами Opera. Пример списков в [Adguard KB](https://adguard-dns.io/kb/ru/general/dns-providers/)
*   **Test URL:** Ссылка, используемая для бенчмарка и выбора самого быстрого сервера при подключении. Можно выбрать любой элемент, который даст ответ 200.
*   **Verbosity Level:** Настройка уровня детализации логов. Работа оболочки и tun2proxy вынесена в категорию Wrapper (App Only). 
*   **LogCat TAG:** slyf0xproxywrapper

### 💻 Ручной режим (Manual CMD Mode)
*   **Включить ручной режим:** При активации переключателя приложение **игнорирует** все графические настройки (регион, SNI, DNS и т.д.).
*   **CMD Preview / Override:** Поле ввода, где вы пишете *любые доступные аргументы запуска бинарника* `opera-proxy`.
*   **Автоматизация:** Путь к бинарному файлу подставляется приложением автоматически, его не нужно вписывать.

### Tun2Proxy DNS (Обработка DNS в туннеле)
Настройка метода обработки DNS-запросов, проходящих через VPN-интерфейс:
*   **Virtual (Fake-IP):** Возвращает виртуальные IP из диапазона `198.18.x.x`. Самый быстрый метод, но может быть несовместим с некоторыми приложениями.
*   **Over TCP (Default):** Инкапсулирует DNS-запросы в TCP и отправляет их через прокси. Обеспечивает максимальную стабильность.
*   **Direct:** DNS-запросы идут напрямую, мимо прокси (может привести к утечкам DNS). (заглушен в UI)

## 🛠 Техническая информация

*   **Android 7.0+** Добавлена обратная совместимость вплоть до Android 5.
*   **Архитектура процессора :** `arm64-v8a` или `armeabi-v7a`. Так же доступен универсальный `universal` APK.
*   **Native Libs:**
    *   `liboperaproxy.so` (Go build) — логика прокси.
    *   `libtun2proxy.so` (Rust build) — перехват TUN-интерфейса.
    *   `lib-native.so` создается во время компиляции APK для связи с tun2proxy.
*   **Ограничение протоколов:** Хотя `tun2proxy` умеет перехватывать UDP, upstream-прокси Opera **не поддерживает UDP**. Весь UDP трафик, попадающий в туннель, будет отброшен (кроме DNS, если включен режим *Over TCP* или *Virtual*, так как он конвертируется/обрабатывается локально).

## 📖 Как пользоваться

1.  **Запуск:** Откройте приложение.
2.  **Выбор региона:** Выберите желаемый регион (Европа, Азия, Америка).
3.  **Приложения:** Нажмите "Выбрать приложения", если хотите пустить через VPN только определенные программы (например, Telegram или Браузер). Если список пуст — проксируется всё устройство.
4.  **Старт:** Нажмите большую кнопку **"Запустить прокси"**.
5.  **Логи:** Следите за статусом подключения в окне логов внизу экрана.

## 📜 Флаги для бинарника opera-proxy
| Argument | Type | Description |
| -------- | ---- | ----------- |
| api-address | String | override IP address of api2.sec-tunnel.com |
| api-client-type | String | client type reported to SurfEasy API (default "se0316") |
| api-client-version | String | client version reported to SurfEasy API (default "Stable 114.0.5282.21") |
| api-login | String | SurfEasy API login (default "se0316") |
| api-password | String | SurfEasy API password (default "SILrMEPBmJuhomxWkfm3JalqHX2Eheg1YhlEZiMh8II") |
| api-proxy | String | additional proxy server used to access SurfEasy API |
| api-user-agent | String | user agent reported to SurfEasy API (default "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36 OPR/114.0.0.0") |
| bind-address | String | proxy listen address (default "127.0.0.1:18080") |
| bootstrap-dns | String | Comma-separated list of DNS/DoH/DoT resolvers for initial discovery of SurfEasy API address. Supported schemes are: `dns://`, `https://`, `tls://`, `tcp://`. Examples: `https://1.1.1.1/dns-query`, `tls://9.9.9.9:853`  |
| cafile | String | use custom CA certificate bundle file |
| config | String | read configuration from file with space-separated keys and values |
| country | String | desired proxy location (default "EU") |
| dp-export | - | export configuration for dumbproxy |
| fake-SNI | String | domain name to use as SNI in communications with servers |
| init-retries | Number | number of attempts for initialization steps, zero for unlimited retry |
| init-retry-interval | Duration | delay between initialization retries (default 5s) |
| list-countries | - | list available countries and exit |
| list-proxies | - | output proxy list and exit |
| override-proxy-address | string | use fixed proxy address instead of server address returned by SurfEasy API |
| proxy | String | sets base proxy to use for all dial-outs. Format: `<http\|https\|socks5\|socks5h>://[login:password@]host[:port]` Examples: `http://user:password@192.168.1.1:3128`, `socks5://10.0.0.1:1080` |
| refresh | Duration | login refresh interval (default 4h0m0s) |
| refresh-retry | Duration | login refresh retry interval (default 5s) |
| server-selection | Enum | server selection policy (first/random/fastest) (default fastest) |
| server-selection-dl-limit | Number | restrict amount of downloaded data per connection by fastest server selection |
| server-selection-test-url | String | URL used for download benchmark by fastest server selection policy (default `https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.min.js`) |
| server-selection-timeout | Duration | timeout given for server selection function to produce result (default 30s) |
| timeout | Duration | timeout for network operations (default 10s) |
| verbosity | Number | logging verbosity (10 - debug, 20 - info, 30 - warning, 40 - error, 50 - critical) (default 20) |
| version | - | show program version and exit |
| socks-mode | - | listen for SOCKS requests instead of HTTP |

## 📜 Для ковыряния в LogCat
- **Linux:** `adb logcat | grep -i -E "slyf0xproxywrapper|tun2proxy|com\.slyf0x\.proxywrapper|com\."`
- **Windows:** `adb logcat | findstr /I /R "slyf0xproxywrapper tun2proxy com\\.slyf0x\\.proxywrapper com\\."`


## ⚠️ Отказ от ответственности

Это приложение является сторонней разработкой и **не связано** с Opera Norway AS. Используйте его на свой страх и риск.
Приложение является графической надстройкой, с реализацией логики для загрузки и взаимодействия с инструментами с открытым исходным кодом.
В приложении применяются "опасные и устаревшие методы загрузки компонентов" по правилам Google, для обратной совместимости. Я Вас предупредил.

*   **Распространение AS IS:** Приложение распространяется по принципу **"как есть"**. Разработчик не несет ответственности за возможные сбои или последствия использования.
*   **Разработка:** Оболочка (Wrapper) улучшается и дорабатывается по мере возможности. Постоянное дополнение это хорошо, но быстро утомляет. В отличие от "портальных" клоунов, мне от Вас ничего не надо, я этот кусок софта в первую очередь разрабатывал для себя. Мне было достаточно того функционала который был даже до внедрения tun2proxy. Но как говорится, Show must go on. Если вам нравится эта программа, пожалуйста поставьте звёздочку репозиторию и обратите внимание на автора компонента opera-proxy, у него много интересных решений на GO.
*   **Запрет на коммерческое использование:** Любое использование данного приложения, его исходного кода, производных работ или интеграций в коммерческих целях, для извлечения прибыли или предоставления платных услуг **СТРОГО ЗАПРЕЩЕНО** лицензией.
*   **Доступный исходный код и модификации:** Базовый исходный код приложения открыт. Без доработок. Исходники перестали обновляться и у портала перестали выходить обновления, просто совпадение, конечно же (changelog тоже было удобно красть). Смотрим в историю в репозитория и смотрим историю обновлений у них (файлы начальные и строчки сравните :D). Вы можете изменять базовый код, дорабатывать или создавать свои версии, **при соблюдении следующих жестких условий**:
    * Вы обязаны сохранить четкое указание авторства **SLY-F0X** opera-proxy-android-wrapper (ОБОЛОЧКИ ЗАПУСКА, ОБВЯЗКУ КОТОРОЙ ПРОСТО УРАЛИ) указание оригинального репозитория с исходным кодом, а также авторов интегрированных компонентов: **Snawoot** (opera-proxy) и проекта **Tun2Proxy**.
    * Любые модифицированные версии должны распространяться на тех же некоммерческих условиях. Никаких запросов на "пожертвования на проект" в UI приложения.
    * Если вы разворачиваете модифицированную версию в сети для других пользователей (даже бесплатно), вы обязаны предоставить им доступ к вашему измененному исходному коду.
    
## CREDITS
*   **Оригинальный [opera-proxy](https://github.com/Snawoot/opera-proxy)** by **[Snawoot](https://github.com/Snawoot)** Репозиторий и исходный код удален. Лицензия MIT.
*   **Tun2Proxy:** [tun2proxy/tun2proxy](https://github.com/tun2proxy/tun2proxy) Лицензия MIT.
*   **ОБОЛОЧКА ЗАПУСКА ДЛЯ ANDROID: opera-proxy-android-wrapper** [SLY-F0X](https://github.com/SLY-F0X/) Лицензия CC BY-NC-SA 4.0 и модифицированная MIT. Запрещено **ЛЮБОЕ** коммерческое использование для извлечения прибыли или предоставления платных услуг.
