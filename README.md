# aleo_deployment

Это скрипт, которой автоматически выполняет все необходимые команды для деплоя приложения в тестнете aleo

Скрипт написан в **Zavod Venture**
Переходите в наш [телеграм](https://t,me/Zavod_Venture), там ещё много интересного.

Кошельки для донатов:

`0x439c834EE3110CeF4874E94125FE950dc8E35e2b` - ERC20

`TSzyryTJkmT9fiMEVBESjA4sh9SpBw16JX` - TRC20

## Генерация адреса кошелька

- В браузере перейдите на https://aleo.tools/ и нажмите кнопку **Generate**
- Сохраните **Address**, **View Key** и **Private Key**, позже они понадобятся

## Получение монет

Для того, чтобы совершить деплой, необходимо запросить монеты у [@AleoFaucet](https://twitter.com/AleoFaucet)

Сделайте твит со следующим текстом:
```
@AleoFaucet send 10 credits to *адрес_кошелька*
```

Через некоторое время @AleoFaucet ретвитнет Ваш запрос. В его ответе будет содержаться URL вида `vm.aleo.org/api/testnet3/transaction...`

- Установите расширение [JSON Beautifier & Editor](https://chrome.google.com/webstore/detail/json-beautifier-editor/lpopeocbeepakdnipejhlpcmifheolpl)
- Перейдите по ссылке, содержащейся в ответе
- Перейдите по пути `object -> execution -> transactions -> 0 -> outputs -> 0 -> value` и скопируйте это значение
- Перейдите на https://aleo.tools/, там выберите раздел **Record**
- В первое поле вставьте **View Key** от кошелька, во второе поле - скопированное на третьем шаге значение
- Сохраните текст, который выдал сайт, в том же месте, где хранятся данные для кошелька

## Подготовка скрипта

- Скачайте zip архив этого репозитория и распакуйте его в удобное место
- Откройте файл `script.sh` с помощью любого текстового редактора и измените строки 1, 2 и 4, вставим между двойными кавычками `Адрес кошелька`, `Приватный ключ` и `Record`, который был получен в прошлом шаге, затем сохраните файл
- [Перенесите](https://telegra.ph/SCP-03-12) файл на linux машину *(работоспособность проверена на ubuntu 22.04)*

## Запуск скрипта

После переноса скрипта на linux машину введите на ней команду `. script.sh`. После этого скрипт начнёт установку всех зависимостей для деплоя *(в процессе потребуется нажать Enter для выбора метода установки Rust и, возможно, ввести пароль от пользователя)*, а позже и сам деплой.

После выполнения скрипта будет выведено название приложения для проверки его на https://aleo.tools