# Краткий Чит-Шит по работе с git и github

## Различие между git и github
**git** - опенсорс проект для контроля версий проектов
**github** - проект компании microsoft, предоставляюший услуги для удаленного и совместного использования репозиториев

## Гайд как создать и загрузить проект на github

### Создание локально
```
mkdir first-project
cd first-project
git init
```

### Добавление файлов для отслеживания
```
nano readme.md
git add readme.md
```

### Проверка статуса
```
git status
```
Убеждаемся, что отображаются совершенные изменения

### Создание коммита
```
git commit -m "Добавлен файл readme.md"
```

### Подключение к github через ssh
```
ssh-keygen -t ed25519 -C "<email>"
cat ~/.ssh/id_ed25519.pub
```
копируем ключ и привязываем к github в соответствующем разделе настроек. проверяем, что удалось подключится, проверяем ключи подлиности от github

```
ssh -T git@github.com
```

### Привязываем удаленный репозиторий к локальному
```
git remote add origin <url ssh>
```
проверяем, что добавилось
```
git remote -v
```

### Отправляем коммит на удаленный сервер
в первый раз:
```
git push -u origin master
```
в последующие разы убираем флаг `-u`

## Хэш, лог и HEAD
### Хэш коммита
Уникальный(практически всегда) идентификатор коммита. Получается из данных коммита и служит некоторой цифровой подписью

### git log
Комманда, выводящая на экран историю коммитов, включая их хэш и комментарий.

`----oneline` - флаг позволяет вывести краткую историю коммитов

### HEAD
Служебный файл, хранящий ссылку на хеш последнего коммита. Можно использовать вместо хеша при запросах к коммандной строке

## Жизненный цикл файлов
```mermaid
graph LR;
	untracked -- "git add" --> staged
	staged -- "Файл изменяется" --> modified
	staged -- "git commit" --> tracked
```
