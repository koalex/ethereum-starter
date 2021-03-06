# Ethereum smart contracts

### GETH (протокол Ethereum, написанный на Go)

##### Установка:

Mac OS

```bash
brew tap ethereum/ethereum
brew install ethereum
```

Ubuntu

```bash
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```

Windows - установить через [инсталлятор](https://ethereum.github.io/go-ethereum/downloads/).

##### Инициализация:

```bash
npm run geth:init
```

##### Запуск:

```bash
npm run geth
```

### Call vs Transaction
**Transaction** - публикуется в сети, выполняется майнерами и если она валидная, то записывается в blockchain.
Она стоит n-ое количество *эфира*. Она асинхронная и возвращает hash транзакции.

**Call** - read-only операция. Выполняется только локально (не публикуется в сети), не требует *эфира* для выполнения.
Выполняется синхронно.
"Constant" keyword in Solidity

### Создание аккаунта майнера
Вернёт адрес Ethereum
```bash
npm run geth:create_account 
```

### genesis.json (первичный блок)

**chainId** - обеспечивает способ совершения транзакций в Ethereum без использования ETC (Ethereum Classic) или тестовой
сети Morden. [EIP 155](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-155.md) предусматривает следующие значения
chainid для разных сетей: основная сеть Ethereum (1), основная сеть Morden / Expanse (2), Ropsten (3), Rinkeby (4),
основная сеть Rootstock(30), тестовая сеть Rootstock (31), Kovan (42), основная сеть Ethereum Classic (61), тестовая
сеть Ethereum Classic (62), приватные цепочки geth (1337 по умолчанию).

**homesteadBlock** - значение 0 указывает на использование релиза Ethereum Homestead. Это второй из основных релизов
Ethereum —  а недавно, 16 октября 2017 года, Ethereum форкнулся на релиз Byzantium.

**eip155Block** - значение 0 указывает, что этот блок поддерживает EIP (Ethereum improvement proposal, предложение об
улучшении Ethereum) номер 155. Предложения EIP описывают стандарты для платформы Ethereum, в том числе ключевые
спецификации протокола, клиентские API и стандарты контрактов.

**eip158Block** - значение 0 указывает, что этот блок поддерживает EIP 158.

**difficulty**  -значение соответствует уровню сложности, которое применяется для поиска случайного значения nonce
к этому блоку. В [этой](https://medium.facilelogin.com/the-mystery-behind-block-time-63351e35603a?gi=ab60df57d463)
статье подробно объясняется, как рассчитывается уровень сложности в Ethereum.

**gasLimit** — это внутренняя единица оплаты для проведения транзакции или контракта в Ethereum. Каждая инструкция,
которая отправляется в виртуальную машину Ethereum Virtual Machine (EVM) для обработки транзакции или смарт-контракта
стоит определённое количество газа. Если транзакция не получает нужного количества газа, то она не пройдёт.
При совершении каждой транзакции в Ethereum вы указываете лимит газа —  максимальное количество, которое могут
использовать все сопутствующие операции для этой транзакции. Параметр gasLimit в блоке определяет общий лимит
всех транзакций в блоке.

**alloc** - параметр для предварительного распределения *эфира* из первичного блока на один или несколько аккаунтов.
В вышеприведённом примере первичного блока весь *эфир* поступает на аккаунт, созданный с самого начала.
