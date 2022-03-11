# Добавление SSH ключа в PhpStorm

1. Создать папку ```C:\Users\<username>\.ssh```
2. Если ключи созданы в PuttyGen, то из них нужно создать ключ в формате OpenSSH:
   - Запустить PuttyGen, выбрать (Load) свой приватный ключ
   - Conversions -> Export OpenSSH key
   - Полученный приватный ключ переименовать в id_rsa, и положить в ```C:\Users\<username>\.ssh```
3. Публичный ключ тоже скопировать в ```C:\Users\<username>\.ssh```, и переименовать в ```id_rsa.pub```
4. В PHPStorm, ```Settings -> Version Control -> Git```, SSH executable: ```Built-in```
