# SchellingToken

## VoterList

Смарт-контракт со белым списком всех голосующих (закрепляющих) за значение.

Интерфейс:
- `is_voter(address)` определить является ли адрес голосующим.

Ограничение:
- централизация контроля за попадание в список. Причина: предотвращение атаки окружением.

## SchellingToken

Смарт-контракт создания запроса, сбора обязательств, раскрытия обязательств, подсчёта медины, награждения веных участнков. 


Эта процедура выглядит следующим образом:

1. Пользователь создаёт:
   1. __Запрос__
   2. Устанавливает __Депозит__
   3. __Время начала и окончания__ срока приёма фиксации
   4. __Время начала и окончания__ срока приёма значений
2. С начала срока приёма фиксации зарегистрированные голосующие отправляют хеши своих решений и депозиты по конкретному Запросу. Хеши имеют вид `hash256 h = sha3(msg.sender, address(this), voteVal, key);`
3. По завершению срока фиксации начинается срок приёма значений. Голосвующие раскрывают свои значения и ключи, использованные для создания хешей на Шаге 2.
4. По завершению срока приёма значений, подсчитывается результат. Избиратели, проголосовавшие за победивший вариант, получают долю от всех депозитов голосов и создателя Запроса.


## TODO

* Сделать интерфейс работы с сервисом из других контрактов.