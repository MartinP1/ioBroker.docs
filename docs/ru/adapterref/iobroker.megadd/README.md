---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translatedFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.megadd/README.md
title: без названия
hash: IROhGk54YUJ2psVEN0iDb9Nnp/gDHwww6G0WkyWEeKs=
---
![логотип](../../../en/adapterref/iobroker.megadd/admin/megad.png) адаптер ioBroker MegaD-2561 =================

![Версия NPM](http://img.shields.io/npm/v/iobroker.megadd.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.megadd.svg)
![NPM](https://nodei.co/npm/iobroker.megadd.png?downloads=true)

Позволяет контролировать [MegaD-2561](http://www.ab-log.ru/smart-house/ethernet/megad-2561) через Ethernet.

## Английский [по русски](#Русский)
## Установить
```node iobroker.js add megadd```

### Информация
Устройство имеет 38 портов, входы / выходы, DSen (DHT11, DHT22, DS18B20 в портах, 1WBUS, iButton (DS1990A, EM-Marine), Wiegand-26), шину I2C (HTU21D, BMP180, BH1750, TSL2591, SSD1306, MCP23008 ).
Чтобы прочитать состояние порта вызова

```http://mega_ip/sec/?pt=4&cmd=get``` , where sec is password (max 3 chars), 4 is port number
The result will come as "ON", "OFF" or analog value for analog ports

To set the state call:
```http://megad_ip/sec/?cmd=2:1``` , where sec is password (max 3 chars), 2 is port number, and 1 is the value
For digital ports only 0, 1 and 2 (toggle) are allowed, for analog ports the values from 0 to 255 are allowed

The device can report the changes of ports to some web server in form
```http://ioBroker:80/?pt=6```  , where 6 is the port number

### Configuration

- IP: IP address of MegaD-2561;
- MegaD-2561 Name: Name of the MegaD-2561 to assign the port changes, e.g. "DevA". If no name set the adapter instance will be used for that;
- Port: Listening port on ioBroker. Default value: 80.
- Poll interval: poll interval in seconds. All configured input ports will be polled in defined interval;
- Password: password to access the device (max 3 characters). Default value "sec";

MegaD-2561 can report about changes on some ports if configured.
You can configure something like that "http://ioBrokerIP/instance" on MegaD-2561 in "Net"-Field and MegaD-2561 will send reports like this one "http://ioBrokerIP/instance/?pt=7" to ioBroker.
That means the button on port 7 was pressed. ioBroker expects instance number (e.g. "0") or defined name of MegaD-2561 (e.g. "DevA"). The "Net" field will look like: "http://192.168.0.8/0/".

### Ports
All ports, that are desired to be used must be configured in right order. Following settings must be set for every port:

- Name: name of the port. Used by ioBroker;
- Input: Is the port INPUT(true) or output(false);
- Switch: Is the port can be ON or OFF (in this case value = TRUE) or just used to send the reports about button press (FALSE);
- Digital: Analog or digital port. ioBroker expects analog ports with range from 0 to 255.
- Offset: offset for the **analog** port.
- Factor:  multiply factor for **anaolog** port.
- Long press: detect long press on digital port (port have to be SWITCH type)
- Double click ms: interval for detection of double click

For input:
```

ioBrokerValue = MegaValue * factor + offset;

```

For output:
```

MegaValue = (ioBrokerValue - смещение) / коэффициент;

```

To get the range of the analog value from 100 to 500 set the factor as 400 and offset = 100.

**The order of the ports is very important. The port in first row will be associated with P0 in MegaD-2561. In row number 14 with P13.**

-------------------
## Русский
Подробную документацию можно найти здесь: [http://www.ab-log.ru/smart-house/ethernet/megad-2561](http://www.ab-log.ru/smart-house/ethernet/megad-2561)

### Настройки

- IP Адрес устройства: IP адрес MegaD-2561;
- MegaD Имя: Имя MegaD-2561 устройства для идентификации сообщений о смене состояния порта от MegaD-2561, например "DevA". Если имя не задано, то для этих целей будет использоватся номер инстанции драйвера.;
- ioBroker веб-порт: Порт на котором ioBroker разворачивает веб сервер для приёма сообщений от MegaD-2561. Значение по умолчанию: 80.
- Интервал опроса (сек): инетрвал опроса портов в секундах;
- MegaD-2561 Пароль: пароль для доступа на MegaD-2561 (максимально 3 символа). Значение по умолчанию: "sec";
- Интервал для длинного нажатия (мс): если отжатие после нажатия кнопки произошло позже указанного интервала, то сгенерируется длинное нажатие;
- Интервал двойного нажатия (мс): если между нажатиями пройдет меньше указанного времени, то сгенерируется двойное нажатие;

В сетевых настройках MegaD-2561 можно сконфигуририровать IP-адрес ioBroker. При каждом нажатии на кнопку MegaD-2561 сообщает ioBroker (restAPI) номер сработавшего входа.

Выглядит запрос примерно следующим образом:
´´´http://192.168.0.250/0/?pt=7´´´

### Порты
Необходимо сконфигурироваь все порты, которые должны быть видимы в ioBorker. Для каждого порта необходимо настроить следующее:

- Имя: имя порта. Исползуется в ioBroker для создание объектов;
- Вход: является ли порт входом (true) или выходом(false);
- Переключатель: Может ли порт быть в положениях ВКЛ и ВЫКЛ (в этом случае значение TRUE) или он просто используется для сигнализирования нажатия на кнопку (FALSE);
- Цифровой: Цифровой или аналоговый порт. ioBroker ожидает значени с аналогового порта в промежутке от 0 до 255.
- Множитель:  множитель для значения **аналогового** порта.
- Сдвиг: сдвиг для значения **аналогового** порта.
- Длинное нажатие: если активировано, то порт будет генерировать событие "длинное нажатие" в объекте port_long (Порт должен быть цифровым и иметь тип "Переключатель")
- Двойное нажатие: если активировано, то порт будет генерировать событие "double click" в объекте port_double

Для выхода:

```

MegaЗначение = (ioBrokerЗначение - Сдвиг) / Множитель;

```

Для входа:

```

ioBrokerЗначение = МегаЗначение * Множитель + Сдвиг;

```

Например, что бы получить интервал значений от 100 до 500 нужно установить сдиг 100 и множитель 400.

Только аналоговые порты принимают во внимание Множитель и Сдвиг.

**Порядок портов очень важен. Порт в первой колонке таблицы ассоциируется с портом P0 на MegaD-2561. Порт в колонке 14 с P13.**

## Changelog
### 0.4.0 (2018-05-15)
* (ausHaus) fix DSen port (W26)

### 0.3.8 (2018-02-20)
* (ausHaus) add I2C Bus scan for ANY port settings

### 0.3.5 (2018-02-15)
* (ausHaus) add 1WBUS, Display port settings

### 0.3.2 (2018-01-29)
* (ausHaus) add DSen port settings (W26)

### 0.3.1 (2017-11-29)
* (ausHaus) small fix

### 0.3.0 (2017-11-29)
* (ausHaus) add I2C Bus port expander (MC23008, MC23017, PCA9685)

### 0.2.2 (2017-06-23)
* (ausHaus) add display settings (Bright)

### 0.2.0 (2017-03-20)
* (ausHaus) add I2C Bus sensor (BMx280)

### 0.1.9 (2017-03-17)
* (ausHaus) add files

### 0.1.8 (2017-03-16)
* (ausHaus) add 1WBUS

### 0.1.7 (2017-03-16)
* (ausHaus) fix README

### 0.1.5 (2017-02-18)
* (ausHaus) add I2C Bus (SSD1306, MCP23008)

### 0.1.3 (2017-01-07)
* (ausHaus) add I2C Bus (HTU21D, BH1750, TSL2591)

### 0.1.2 (2016-11-23)
* (ausHaus) add DS2413 out A/B

### 0.1.0 (2016-11-01)
* (ausHaus) initial commit
