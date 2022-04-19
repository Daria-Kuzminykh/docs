# Автозапуск eslint и вебхук в mattermost

### 1. Добавляем в `.gitlab-ci.yml`

```yaml
stages:
  - lint

eslint:
  stage: lint
  script:
    - yarn
    - yarn eslint "src/{**/*,*}.{js,ts,jsx,tsx}" --quiet
```

### 2. Добавляем команду `yarn eslint`

Добавляем в `package.json` команду, чтобы можно было принудительно локально проверить ошибки разработчику

```json
{
  "scripts": {
    "eslint": "eslint \"src/{**/*,*}.{js,ts,jsx,tsx}\" --quiet"
  }
}
```


### 3. Добавляем вебхук в mattermost

Идем в меню маттермоста -> Integrations -> Incoming Webhooks -> Add Incoming Webhook

Заполняем `Title` аля `my-project-pipeline-fails`, выбираем нужный канал.

Жмем добавить, получаем ссылку вебхука.

### 4. Отправка вебхука в GitLab

Заходим внутри проекта: My Project -> Settings -> Integrations -> Mattermost notifications

Оставляем галочки `Active`, `Pipeline`, `Notify only broken pipelines`

В `Webhook` вводим полученную на прошлом шаге ссылку

В `Pipeline` вводим имя канала маттермоста

Сохраняем, готово ✌️
