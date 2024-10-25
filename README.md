# Интернет-магазин по продаже игр "KupiGame"
Состав команды:
+ Еремеев Сергей - 3 курс ИВТ-22-22
+ Галкин Роман - 3 курс ИВТ-22-22
+ Павлов Даниил - 3 курс ИВТ-22-22
+ Алексеев Даниил - 3 курс ИВТ-22-22

### СОДЕРЖАНИЕ РАБОТЫ



1. [Введение](#введение)
   - [Описание интернет-магазина KupiGame](#описание-интернет-магазина-kupgigame)
   - [Постановка задачи](#постановка-задачи)
   - [Цели и предложение безопасности (ЦПБ)](#цели-и-предложение-безопасности-цпб)
   - [Защищаемые сведения](#защищаемые-сведения)

2. [Архитектура интернет-магазина](#архитектура-интернет-магазина)
   - [Компоненты решения](#компоненты-решения)
   - [Описание алгоритмов взаимодействия](#описание-алгоритмов-взаимодействия)
   - [Схема взаимодействия компонентов интернет-магазина (до кибериммунизации)](#схема-взаимодействия-компонентов-интернет-магазина-до-кибериммунизации)
   - [Угрозы безопасности сайта по списку OWASP](#угрозы-безопасности-сайта-по-списку-owasp)
   - [Описание сценариев, при которых ЦБ нарушаются](#описание-сценариев-при-которых-цб-нарушаются)

3. [Кибериммунизация интернет-магазина](#кибериммунизация-интернет-магазина)
   - [Принципы кибериммунизации](#принципы-кибериммунизации)
   - [Изменения в архитектуре после внедрения кибериммунизации](#изменения-в-архитектуре-после-внедрения-кибериммунизации)
   - [Методы противодействия основным угрозам OWASP](#методы-противодействия-основным-угрозам-owasp)
   - [Реализация Zero Trust модели](#реализация-zero-trust-модели)
   - [Мониторинг и анализ поведения системы](#мониторинг-и-анализ-поведения-системы)
   - [Автоматическое реагирование на инциденты безопасности](#автоматическое-реагирование-на-инциденты-безопасности)

4. [Заключение](#заключение)
---

<a name="введение"></a>
## Введение
В данном проекте разрабатывается интернет-магазин **KupiGame**, который предоставляет возможность пользователям приобретать цифровые товары, такие как игры и программное обеспечение. Основное внимание уделено не только функциональной части магазина, но и аспектам безопасности, чтобы защитить данные пользователей и предотвратить потенциальные угрозы. Веб-сайт, на котором продаются игры, обычно состоит из нескольких компонентов, которые работают вместе, обеспечивая удобство взаимодействия с пользователем. Архитектуру такого веб-сайта можно разбить на следующие уровни: Веб-интерфейс: это часть веб-сайта, ориентированная на пользователя, созданная с использованием HTML, CSS и JavaScript. Он предоставляет пользователям интерактивный интерфейс для просмотра и покупки игр. Механизм шаблонов: механизм шаблонов, такой как Handlebars или Mustache, используется для отображения динамического контента на веб-сайте.

<a name="описание-интернет-магазина-kupgigame"></a>
### Описание интернет-магазина KupiGame
KupiGame — это платформа для продажи цифровых продуктов. В магазине реализована система регистрации, выбора и оплаты товаров, а также доступ к приобретенному контенту через уникальные ключи или лицензии.
KupiGame — это интернет-магазин, специализирующийся на продаже цифровых игр, программного обеспечения и игровых аксессуаров. Мы предлагаем широкий ассортимент товаров, включая новинки, популярные хиты и инди-игры. Наша платформа обеспечивает удобный и безопасный процесс покупки, а также регулярные акции и скидки для наших клиентов. Он стремится предоставить высококачественный сервис, быстрые доставки и поддержку пользователей, чтобы каждый мог легко найти и приобрести любимые игры. KupiGame — ваш надежный помощник в мире цифровых развлечений.

<a name="постановка-задачи"></a>
### Постановка задачи
Задача проекта — создание безопасной платформы для совершения покупок и защиты данных пользователей от утечек и взломов.
Задача проекта заключается в создании безопасной платформы для онлайн-покупок, которая гарантирует защиту данных пользователей от утечек и взломов. В центре нашего подхода — использование современных технологий шифрования для защиты личной информации, таких как платежные данные и учетные записи. Мы интегрируем многоуровневую аутентификацию, чтобы обеспечить дополнительную безопасность при входе на платформу.

<a name="цели-и-предложение-безопасности-цпб"></a>
### Цели и предложение безопасности (ЦПБ)
Основные цели безопасности:
- Аутентификация с двухфакторной аутентификацией.
- Шифрование данных.
- Обновление системы и мониторинг уязвимостей.
- Защищенные каналы для финансовых транзакций.

<a name="защищаемые-сведения"></a>
### Защищаемые сведения
К защищаемым данным относятся:
- Персональные данные пользователей.
- Платежная информация.
- Информация о заказах и покупках.



---

<a name="архитектура-интернет-магазина"></a>
## Архитектура интернет-магазина

Архитектура интернет-магазина **KupiGame** описывает внутренние компоненты системы, их взаимодействие, а также учитывает потенциальные угрозы безопасности и методы их предотвращения. Этот раздел содержит детальный обзор технической реализации.

Архитектура интернет-магазина **KupiGame** без кибериммунизации включает несколько ключевых компонентов, каждый из которых играет свою роль в обеспечении функциональности и безопасности платформы. На клиентском уровне интерфейс разработан для удобства пользователей, с понятной навигацией и доступом к различным категориям товаров. Пользователи могут легко просматривать игры, добавлять их в корзину и оформлять заказы. Серверная часть состоит из основных серверов, которые обрабатывают запросы клиентов и хранят данные о пользователях и продуктах. Защита этой части обеспечивается брандмауэрами и базовыми системами обнаружения вторжений, но без применения продвинутых технологий. База данных хранит информацию о пользователях, транзакциях и товарах. Данные шифруются, но могут не использовать самые современные методы защиты. Доступ к базе осуществляется через API, однако могут отсутствовать строгие правила управления доступом. Транзакции обрабатываются через стандартные протоколы безопасности, такие как HTTPS, что защищает данные во время передачи. Однако отсутствие многоуровневых защитных механизмов может сделать систему уязвимой для атак. Мониторинг трафика ограничивается основными инструментами, что снижает возможность выявления аномалий и угроз в реальном времени. В случае атаки реакции могут быть замедлены, и это повышает риск ущерба. Сегментация сети в данной архитектуре может отсутствовать, что делает всю систему более подверженной атакам на уровне целого магазина. Все компоненты могут быть связаны, и это создает уязвимости. Образовательные инициативы для сотрудников минимальны, что снижает осведомленность команды о киберугрозах и их последствиях. Таким образом, архитектура KupiGame без кибериммунизации фокусируется на базовых элементах работы интернет-магазина, однако не обеспечивает должного уровня защиты данных и устойчивости к потенциальным угрозам.

<a name="компоненты-решения"></a>
### Компоненты решения
Основные компоненты системы интернет-магазина:
- Бэкенд (серверная часть), отвечающий за обработку запросов, управление данными и взаимодействие с базой данных.
- Фронтенд (клиентская часть), интерфейс пользователя для навигации по сайту и взаимодействия с системой.
- База данных, которая хранит информацию о товарах, пользователях и заказах.
- Система обработки платежей для проведения безопасных финансовых транзакций.
- Модуль безопасности для защиты данных пользователей и предотвращения кибератак.

<a name="описание-алгоритмов-взаимодействия"></a>
### Описание алгоритмов взаимодействия
Алгоритмы взаимодействия между компонентами включают:
- Обработку пользовательских запросов с фронтенда и передачу данных на сервер.
- Взаимодействие с базой данных для извлечения, изменения и хранения данных.
- Интеграция с платёжной системой для безопасного проведения транзакций.
- Проверка подлинности пользователей и авторизация их действий в системе.

<a name="схема-взаимодействия-компонентов-интернет-магазина-до-кибериммунизации"></a>
### Схема взаимодействия компонентов интернет-магазина (до кибериммунизации)
На данном этапе архитектуры компоненты взаимодействуют следующим образом:
- Пользователь отправляет запрос через фронтенд.
- Бэкенд обрабатывает запрос и взаимодействует с базой данных для предоставления соответствующих данных.
- При оплате происходит обращение к платёжной системе.
- Защита осуществляется базовыми методами (шифрование данных, стандартные методы аутентификации).
Этот раздел включает детализированную схему архитектуры без внедрения дополнительных кибериммунных средств защиты.

<a name="угрозы-безопасности-сайта-по-списку-owasp"></a>
### Угрозы-безопасности-сайта-по-списку-owasp
1. SQL-инъекции: Эта угроза возникает, когда злоумышленник вводит вредоносный SQL-код в поля ввода, например, в форму входа или поиска. Это может позволить получить доступ к базе данных, извлекать, изменять или удалять данные пользователей, что приводит к утечкам личной информации и финансовых данных.

2. Кросс-сайтовый скриптинг (XSS): В этой ситуации злоумышленник может внедрить вредоносные скрипты в контент, который отображается пользователям. При посещении сайта пользователи могут случайно выполнить этот скрипт, что может привести к кражам сессий, изменению данных или перенаправлению на фишинговые сайты.

3. Неправильная настройка безопасности: Неправильная конфигурация серверов и приложений может оставить уязвимости, которые злоумышленники могут использовать для получения несанкционированного доступа. Это может включать использование стандартных паролей, открытые порты или неправильные настройки брандмауэра.

4. Несанкционированный доступ: Отсутствие должной аутентификации и авторизации может позволить злоумышленникам получить доступ к защищенным частям сайта. Это может привести к компрометации учетных записей администраторов, что открывает доступ к критически важной информации и управлению сайтом.

5. Уязвимости при передаче данных: Если данные не шифруются при передаче, злоумышленники могут перехватить информацию, такую как личные данные и платежные реквизиты. Это угрожает конфиденциальности пользователей и может привести к финансовым потерям.

6. Инъекции кода: Это включает в себя возможности внедрения кода в приложения или системы, что может привести к исполнению вредоносных операций на сервере. Это может вызвать сбой работы сайта, кражу данных или запуск атак на другие системы.

7. Уязвимости сторонних компонентов: Если магазин использует сторонние библиотеки или плагины, они могут содержать уязвимости. Необновленные или плохо защищенные компоненты могут стать целью злоумышленников.

8. Недостаток логирования и мониторинга: Если в магазине отсутствуют надлежащие механизмы логирования действий пользователей и мониторинга системы, злоумышленники могут легко совершать атаки, не оставляя следов. Это затрудняет выявление и реагирование на инциденты безопасности.

9. Фишинг и социальная инженерия: Злоумышленники могут использовать методы социальной инженерии, чтобы обманом получить доступ к учетным данным пользователей. Например, рассылка фишинговых писем с просьбой подтвердить учетные данные может привести к компрометации аккаунтов.

10. Атаки отказа в обслуживании (DDoS): Эти атаки направлены на перегрузку сервера запросами, что может сделать сайт недоступным для пользователей. Это приводит к потере бизнеса и ухудшению репутации.

<a name="описание-сценариев-при-которых-цб-нарушаются"></a>
### Описание сценариев, при которых ЦБ нарушаются
Возможные сценарии нарушения безопасности:

+ Сценарий 1: Злоумышленник использует SQL-инъекцию для получения доступа к базе данных магазина. Вводя вредоносный код в форму входа, он извлекает личные данные пользователей, включая имена, адреса и платежные реквизиты. Это приводит к утечке конфиденциальной информации и нарушению доверия клиентов.

+ Сценарий 2: В результате атаки кросс-сайтового скриптинга (XSS) на страницу с отзывами, злоумышленник внедряет скрипт, который крадет куки пользователей. Пользователи, посетившие страницу, автоматически отправляют свои куки злоумышленнику, что позволяет ему получить доступ к их учетным записям и совершать покупки от их имени.

+ Сценарий 3: Сторонний плагин, используемый в магазине, оказывается уязвимым. Злоумышленник использует эту уязвимость, чтобы получить доступ к администраторскому интерфейсу, изменяет цены на товары и наносит ущерб бизнесу, создавая недовольство среди клиентов.

+ Сценарий 4: В результате недостаточной аутентификации злоумышленник получает доступ к учетной записи администратора, используя простой пароль. Он изменяет настройки безопасности сайта, отключает защитные механизмы и открывает доступ к внутренним данным, что приводит к полной компрометации системы.

+ Сценарий 5: Магазин становится целью атаки DDoS, когда злоумышленник отправляет миллионы запросов к серверу, перегружая его. В результате сайт становится недоступным для пользователей, что приводит к потере продаж и ухудшению репутации.

Эти сценарии подчеркивают важность защиты конфиденциальной информации и необходимости внедрения эффективных мер безопасности для минимизации рисков для интернет-магазина.

<a name="кибериммунизация-интернет-магазина"></a>
## Кибериммунизация интернет-магазина
Кибериммунизация — это подход к разработке, при котором система становится устойчивой к атакам, обеспечивая возможность продолжать функционировать даже при попытке взлома. Внедрение кибериммунных технологий позволяет интернет-магазину **KupgiGame** минимизировать риск компрометации системы и защитить данные пользователей.

Кибериммунизация интернет-магазина **KupiGame** представляет собой комплексный подход к обеспечению безопасности, направленный на защиту данных пользователей и устойчивость к кибератакам. Этот процесс включает в себя внедрение многоуровневых мер защиты, современных технологий и постоянного обучения сотрудников.

На первом уровне кибериммунизации осуществляется анализ текущей инфраструктуры безопасности. Это включает в себя аудит систем и выявление уязвимостей, что позволяет понять слабые места и области для улучшения. После анализа разрабатывается стратегический план, который включает в себя обновление программного обеспечения, применение современных средств защиты и внедрение лучших практик в области безопасности.

Одной из ключевых составляющих кибериммунизации является использование многофакторной аутентификации для всех пользователей, особенно для администраторов и сотрудников с доступом к критически важным данным. Это существенно затрудняет злоумышленникам возможность несанкционированного доступа к учетным записям.

Для защиты данных при передаче используется шифрование, что обеспечивает безопасность платежной информации и личных данных пользователей. Все взаимодействия с сайтом должны проходить через защищенные протоколы, такие как HTTPS. Кроме того, данные, хранящиеся в базе данных, также шифруются, что минимизирует риски утечки информации.

Внедрение системы мониторинга и обнаружения вторжений позволяет оперативно реагировать на подозрительную активность. Эти системы анализируют трафик в реальном времени и могут выявлять аномалии, что способствует быстрому выявлению и устранению угроз. Регулярные тестирования на проникновение помогают в выявлении уязвимостей и недочетов в защите.

Образование сотрудников играет важную роль в кибериммунизации. Проводятся регулярные тренинги и семинары по вопросам кибербезопасности, где сотрудники обучаются методам предотвращения фишинга, социальной инженерии и других распространенных угроз. Это формирует культуру безопасности внутри компании, повышая осведомленность команды.

Важно также регулярно обновлять программное обеспечение и системы безопасности, устанавливая последние патчи и обновления. Это предотвращает использование известных уязвимостей и помогает поддерживать высокие стандарты безопасности.

В рамках кибериммунизации осуществляется создание плана реагирования на инциденты, который включает четкие инструкции по действиям в случае возникновения кибератак. Это позволяет быстро и эффективно реагировать на инциденты, минимизируя последствия и восстанавливая нормальную работу магазина.

Таким образом, кибериммунизация KupiGame включает в себя комплексный подход к безопасности, основанный на анализе, технологии, обучении сотрудников и разработке четких планов действий, что обеспечивает защиту данных пользователей и устойчивость к киберугрозам.


<a name="изменения-в-архитектуре-после-внедрения-кибериммунизации"></a>
### Изменения в архитектуре после внедрения кибериммунизации
После внедрения кибериммунизации архитектура интернет-магазина претерпела значительные изменения:
- Добавлены многослойные механизмы безопасности, включая микросервисы с изоляцией данных.
- Усилено шифрование данных как на уровне передачи, так и на уровне хранения.
- Внедрены новые протоколы обмена данными между компонентами с защитой от компрометации.
- Введена сегментация сети для изоляции критически важных ресурсов.
### Архитектура интернет-магазина после кибериммунизации
Архитектура интернет-магазина **KupiGame** после кибериммунизации построена на принципах безопасности, масштабируемости и удобства для пользователей. Она включает несколько ключевых компонентов, каждый из которых играет важную роль в обеспечении защиты и эффективной работы платформы.

Клиентский интерфейс разработан с акцентом на безопасность и удобство. Все взаимодействия пользователей с сайтом проходят через защищенные каналы (HTTPS), а для входа в учетные записи используется многофакторная аутентификация. Интерфейс интуитивно понятен и адаптивен, что позволяет пользователям легко находить нужные товары и совершать покупки.

На серверном уровне архитектура основана на распределенных системах и микросервисах. Каждый компонент системы работает независимо, что повышает устойчивость и облегчает масштабирование. Используются контейнеризированные решения (например, Docker), что позволяет быстро разворачивать и обновлять приложения, а также минимизировать риски, связанные с уязвимостями.

База данных защищена с использованием современных методов шифрования и токенизации. Доступ к базе осуществляется через контролируемые API с строгими правилами управления доступом, что минимизирует риски утечек информации. Регулярные резервные копии и шифрование данных на уровне хранения обеспечивают дополнительную защиту.

Системы мониторинга и обнаружения вторжений интегрированы в архитектуру, обеспечивая постоянный анализ трафика и активности на сайте. Эти системы могут автоматически реагировать на подозрительную активность, блокируя потенциальные атаки и предупреждая администраторов о возможных угрозах.

Сегментация сети разделяет различные компоненты системы, изолируя критически важные элементы от менее защищенных. Это позволяет минимизировать последствия потенциальных атак и повысить общую безопасность.

Образовательные инициативы для сотрудников поддерживаются регулярными тренингами и симуляциями атак, что позволяет формировать культуру безопасности и повышать осведомленность команды о киберугрозах.

Архитектура **KupiGame** после кибериммунизации представляет собой надежную и гибкую платформу, которая не только обеспечивает высокий уровень защиты данных пользователей, но и поддерживает стабильную работу интернет-магазина в условиях постоянных угроз.

### Изменения в архитектуре

1. Микросервисная архитектура: Переход на микросервисы позволяет изолировать функциональные модули, такие как управление пользователями, обработка платежей и каталог товаров. Это упрощает масштабирование и обновление отдельных компонентов без влияния на всю систему.

2. Улучшенная аутентификация: Внедрение многофакторной аутентификации для всех пользователей, включая администраторов, повышает уровень безопасности учетных записей и защищает от несанкционированного доступа.

3. Расширенные механизмы шифрования: Использование современных методов шифрования для данных как при передаче, так и при хранении. Это включает шифрование чувствительных данных, таких как платежные реквизиты и личная информация пользователей.

4. Системы мониторинга и обнаружения вторжений: Внедрение технологий для постоянного анализа трафика и обнаружения аномалий в реальном времени. Это позволяет оперативно реагировать на потенциальные угрозы и минимизировать ущерб.

5. Сегментация сети: Создание изолированных сетевых сегментов для различных компонентов системы, что уменьшает вероятность того, что атака на один компонент затронет другие.

6. Регулярные обновления и патчи: Установлены процессы для регулярного обновления программного обеспечения и установки патчей безопасности, что защищает от известных уязвимостей.

7. Образовательные программы: Внедрение регулярных тренингов и симуляций для сотрудников по вопросам кибербезопасности, что повышает общую осведомленность и готовность к реагированию на инциденты.

8. План реагирования на инциденты: Разработка четких процедур для быстрого реагирования на инциденты безопасности, что позволяет минимизировать последствия возможных атак.


<a name="методы-противодействия-основным-угрозам-owasp"></a>
### Методы противодействия основным угрозам OWASP
Для противодействия угрозам безопасности, указанным в списке OWASP, в рамках кибериммунизации были применены следующие меры:
- Использование защищённых алгоритмов верификации и аутентификации, предотвращающих атаки на сессии.
- Полная защита от инъекций благодаря строгой проверке вводимых данных и применению параметризированных запросов.
- Повышение контроля доступа с помощью ролифицированной системы авторизации и модели минимальных привилегий.

<a name="реализация-zero-trust-модели"></a>
### Реализация Zero Trust модели
Модель Zero Trust внедрена для обеспечения полной проверки каждого запроса независимо от его происхождения. Принципы модели включают:
- Проверка всех участников системы, включая пользователей, устройства и сетевые компоненты.
- Применение политики наименьших привилегий для пользователей и процессов.
- Постоянный мониторинг и верификация активности системы.

<a name="мониторинг-и-анализ-поведения-системы"></a>
### Мониторинг и анализ поведения системы
Модуль мониторинга отслеживает активность системы в реальном времени для выявления подозрительных действий. Основные направления мониторинга:
- Анализ сетевого трафика на предмет аномалий.
- Мониторинг доступа к критически важным данным и системам.
- Автоматическое уведомление о потенциальных инцидентах безопасности.

<a name="автоматическое-реагирование-на-инциденты-безопасности"></a>
### Автоматическое реагирование на инциденты безопасности
Для быстрой реакции на угрозы внедрена система автоматического реагирования. Основные функции:
- Автоматическая блокировка учётных записей при подозрительных действиях.
- Изоляция скомпрометированных компонентов системы для предотвращения распространения угрозы.
- Автоматический перезапуск уязвимых сервисов и уведомление администраторов о необходимости дополнительного анализа.

<a name="заключение"></a>
## Заключение
Проект интернет-магазина **KupgiGame** продемонстрировал важность всестороннего подхода к разработке и защите веб-приложений. В ходе работы была создана безопасная платформа для продажи цифровых товаров, обеспечивающая надежную защиту данных пользователей и стабильное функционирование системы. 

Разработка архитектуры, ориентированной на кибериммунные принципы, позволила усилить безопасность и снизить вероятность компрометации системы. Применение рекомендаций OWASP помогло минимизировать основные угрозы безопасности, а внедрение модели Zero Trust и автоматических механизмов реагирования значительно повысило устойчивость системы к современным киберугрозам.

Основной вывод данного проекта заключается в том, что только интеграция продвинутых методов защиты и мониторинга позволяет создать надежный и устойчивый интернет-магазин, который сможет противостоять постоянно меняющимся угрозам в киберпространстве.
