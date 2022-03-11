# Настройка окружения

## Установка ПО

Перед началом работы у каждого программиста должно быть установлен следующий софт:

- Система контроля версий Git;
- Желательно Git клиент ([SourceTree](https://www.sourcetreeapp.com/), [TortoiseGit](https://tortoisegit.org/), [SmartGit](https://www.syntevo.com/smartgit/download/) или другой);
- IDE [PhpStorm](https://www.jetbrains.com/ru-ru/phpstorm/);
- Для JS разработчиков — [Node.js](https://nodejs.org/en/download/) и [Yarn](https://classic.yarnpkg.com/lang/en/docs/install/);
- Для тестирования http запросов — [Postman](https://www.postman.com/downloads/);

Из IDE для нас в приоритете PhpStorm (или WebStorm). Другие тоже можно использовать, но тогда вам самому нужно
будет разбираться в его настройки и подключении линтеров, шаблонов кода и прочего. Поэтому если вы новичок — лучше
поставить проверенный PhpStorm.

## Настройка SSH ключа

Для правильной работы с Git необходимо в настройках своего профиля GitLab прописать публичный ssh ключ.

Для Linux/MacOS пользователей его можно взять из `~/.ssh/id_rsa.pub`. Для пользователей Windows путь немного сложнее,
но есть инструкции:

- [Создание SSH ключа и добавление его в TortoiseGit](setup-ssh-tortoise.md)
- [Добавление SSH ключа в PhpStorm](setup-ssh-phpstorm.md)

## Настройка IDE (PhpStorm)

Хотя мы и придерживаемся общепринятых конфигураций, некоторые настройки все же необходимо произвести перед началом
работы в компании:

### 1. Использование одинарных кавычек

По Code Style в компании мы решили использовать по-умолчанию одинарные кавычки, если ничего этому не препятствует
(нет переменных в строке или одинарных кавычек в тексте). В PhpStorm эта настройка ставится тут: Preferences -> Editor -> Code Style ->

1. `JavaScript -> Punctuation -> “Use [single] quotes in new code”`;
2. `TypeScript -> Punctuation -> “Use [single] quotes in new code”`;
3. `HTML -> Other -> Generate quote marks -> [single]`.

### 2. Включаем линтер кода

Очень важно следить за чистотой кода и приводить его в соответствие с замечаниями, которые подсказывает линтер.
Чтобы его включить, перейдите в следующий раздел: `Preferences -> Languages & Frameworks -> JavaScript -> Code Quality Tools -> ESLint`

1. Установите `“Automatic ESLint configuration”`;
2. И поставьте флажок `“Run eslint --fix” on save”`, чтобы IDE самостоятельно исправляла замечания при сохранении файла.

### 3. Создание шаблонов кода

Помним, что мы не хотим тратить время на рутинные задачи. Создание пачки файлов для React компонентов
(dir + ts + tsx + scss files) — одна из таких рутинных задач.

Для создания шаблона кода для такой задачи необходимо перейти в настройки: `Preferences -> File and Code Templates -> “+” (Create Template)`

**Основной шаблон:**

- Name: `ReactGroup`
- Extension: `ts`
- File name: `${NAME}/index.ts`
- Content:

```
import ${NAME} from './${NAME}';
export default ${NAME};
```

**Вложенный шаблон для SCSS (Create Child Template File):**

- File name: `${NAME}/${NAME}.scss`
- Extension: `scss`
- Content:

```
@import 'style/variables';

.${NAME} {
}
```

**Вложенный шаблон для TS (Create Child Template File):**

- File name: `${NAME}/${NAME}.tsx`
- Extension: `tsx`
- Content:

```
import React from 'react';
import useBem from '@steroidsjs/core/hooks/useBem';

import './${NAME}.scss';

export default function ${NAME}() {
const bem = useBem('${NAME}');

    return (
        <div className={bem.block()}>
        </div>
    );
}
```
