# Coding Best Practice

## Классы, методы и переменные

**Минимум публичности**

Если переменная используется только в классе и не планируется использовать её во вне, то нужно делать её приватной.
Это относится как к создаваемым переменным класса, так и к методам. Чем меньше публичного - тем проще АПИ и легче
рефакторить код в будущем.

**Полные названия**

По названию переменной/класса/метода должно быть понятно что это и из какой области. Поэтому нельзя сокращать
переменные, например, до wtp, нужно писать полностью - wayToPerfection, ибо через месяц даже сам разработчик уже
забудет свои сокращения.

**Название = смысл**

По названию переменной/класса/метода должно быть понятно что в ней лежит. Если из названия не очевиден тип, то лучше
и тип в название дописывать. Например, по названию переменной $user не понятен тип данных, это может быть array,
object, экземпляр класса (а у некоторых (что очень плохо) даже ИД юзера). Поэтому лучше называть $userModel, если
это гарантированно экземпляр класса и $userId если это идентификатор.

TODO
- Использование констант
- Использование перечислений, BaseEnum
- Комментируйте неочевидные места
- Нет смысла пушить закомментированный код
- гит: названия веток, воркфлоу, как часто пушить..