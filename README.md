# Blogmaker

Это очень простое решение для самостоятельной публикации блогов.

### Dependencies

* pandoc
* rsync

### How to use

Посмотрите каталог [posts](./posts) чтобы понять как должен выглядеть пост. Пост должен быть написан [markdown](https://daringfireball.net/projects/markdown/syntax), и имя файла должно закончиватся на ".md". Дата должна быть в формате (yyyy/mm/dd). Все посты должны быть в дериктории posts.

If you need a post to use MathJaX to format LaTeX equations, add the line

```
[pandoc]: <> (--mathjax)
```

to the config at the top of the post.

Чтобы скомпилировать пост в html, запустите `./publish.py posts/name_of_post.md` (или `./publish.py posts/*` для рекомпиляции всего). Используйте `./publish.py --sync` для загрузки последней версии вашего сайта на сервер (убедитесь, что указали данные вашего сервера, а также название и значок сайта, в [config.md](./config.md)).

Для сервера самая простая настройка — использовать любой VPS, `apt install apache2`, убедитесь, что apache2 запущен, и просто установите в директорию /var/www/html.

### Misc

Credit to https://hackmd.io for CSS styles.
