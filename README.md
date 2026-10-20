# Наследие-Проект - клиентский просмотр

Демонстрация будущей темы WordPress: 586 страниц с услугами, информацией о компании, контактами, лицензиями и всеми записями блога. Сохранены фирменные цвета и логотип. Формы в демонстрации не отправляют обращения.

Исходные файлы статического сайта находятся в архиве `nasledie-client-github-pages.zip`. GitHub Actions проверяет архив, распаковывает его и публикует готовый сайт через GitHub Pages. Адреса страниц, поиск и ресурсы автоматически учитывают имя репозитория.

В репозитории нет базы данных, WordPress, административных файлов, ключей или архива устанавливаемой темы. Изображения статей и подлинные сканы документов загружаются с действующего сайта. Метки `noindex,nofollow` и `robots.txt` сохранены для ограничения индексации демонстрации; доступ к ней публичный.

## Публикация

1. В **Settings > Pages > Build and deployment > Source** выберите **GitHub Actions**.
2. Откройте **Actions > Publish client preview**. Сборка запускается при изменениях в `main`; при необходимости выберите **Run workflow**.
3. После успешной сборки адрес сайта отображается в **Settings > Pages** и в результате deployment `github-pages`.

При замене архива нужно обновить `PREVIEW_SHA256` в `.github/workflows/pages.yml`. Workflow проверяет весь архив до выполнения сборки.

## Локальная проверка

Распакуйте архив в отдельный каталог. Нужен Node.js 22 или новее; установка пакетов не требуется.

```text
node prepare-pages.mjs --base /example/ --origin https://owner.github.io
node check-pages.mjs --base /example/ --origin https://owner.github.io
```

Результат записывается в `_site/`. Для размещения на собственном хостинге используйте подходящие `--base` и `--origin`.

Workflow использует [официальные действия GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages).
