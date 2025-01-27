# aleo_deployment

Это скрипт, которой автоматически выполняет все необходимые команды для деплоя приложения в тестнете aleo

Скрипт написан в **Zavod Venture**
Переходите в наш [телеграм](https://t.me/Zavod_Venture), там ещё много интересного.

Кошельки для донатов:

`0x439c834EE3110CeF4874E94125FE950dc8E35e2b` - ERC20

`TSzyryTJkmT9fiMEVBESjA4sh9SpBw16JX` - TRC20

## Генерация адреса кошелька

- В браузере перейдите на https://aleo.tools/ и нажмите кнопку **Generate**
- Сохраните **Address**, **View Key** и **Private Key**, позже они понадобятся

## Подготовка скрипта

- Скачайте zip архив этого репозитория и распакуйте его в удобное место
- Откройте файл `script.sh` с помощью любого текстового редактора и измените строки 1 и 3, вставив между двойными кавычками `Адрес кошелька` и `Приватный ключ`, затем сохраните файл
- [Перенесите](https://telegra.ph/SCP-03-12) файл на linux машину *(работоспособность проверена на ubuntu 22.04)*

Правильно заполненный файл выглядит следующим образом:

![image](https://user-images.githubusercontent.com/127696238/230115045-39ac36fb-4830-4160-aee5-adf67a3dbb23.png)

## Запуск скрипта

После переноса скрипта на linux машину введите на ней команду следующую команду:

```
sudo apt update -y && sudo apt install -y dos2unix && dos2unix script.sh && . script.sh
```

После этого скрипт начнёт установку всех зависимостей для деплоя *(в процессе потребуется нажать Enter для выбора метода установки Rust и, возможно, ввести пароль от пользователя)*, а позже и сам деплой.

В процессе выполнения скрипт самостоятельно получит тестовые токены для деплоя. После этого будет выведено значение **CLIPHERTEXT** и скрипт будет ждать ввода **PLAINTEXT**. Получить его можно следующим образом:

- Заходим на https://aleo.tools/ в раздел Record
- В первое поле вводим то значение, которое выдал скрипт
- Во второе поле вводим `view key` кошелька

Если всё было введено правильно, на сайте появится примерно такой текст:

```
{
  owner: aleo1rhgdu77hgyqd3xjj8ucu3jj9r2krwz6mnzyd80gncr5fxcwlh5rsvzp9px.private,
  gates: 550000000000000u64.private,
  _nonce: 4324037486175223501017904251644658173467860078798396792350707407904752217504group.public
}
```

Копируем его и убираем все переносы строк (пробелы после запятых и двуеточий сохраняем), чтобы получилось вот так:

```
{owner: aleo1rhgdu77hgyqd3xjj8ucu3jj9r2krwz6mnzyd80gncr5fxcwlh5rsvzp9px.private, gates: 550000000000000u64.private, _nonce: 4324037486175223501017904251644658173467860078798396792350707407904752217504group.public}
```

Полученный текст вставляем в машину и нажимаем Enter. После этого скрипт продолжит работу и сделает деплой.

После выполнения скрипта будет выведено название приложения для проверки его на https://aleo.tools (Раздел **REST API**, блок **Get Program**. В поле ввести название, которое выдал скрипт, + ".aleo")
