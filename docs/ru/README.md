# gin-pgfc
> клей pgfc для gin-gonic

[![GoCard][gc1]][gc2]
 [![GitHub Release][gr1]][gr2]
 [![GitHub code size in bytes][sz]]()
 [![GitHub license][gl1]][gl2]

[gc1]: https://goreportcard.com/badge/apisite/gin-pgfc
[gc2]: https://goreportcard.com/report/github.com/apisite/gin-pgfc
[gr1]: https://img.shields.io/github/release/apisite/gin-pgfc.svg
[gr2]: https://github.com/apisite/gin-pgfc/releases
[sz]: https://img.shields.io/github/languages/code-size/apisite/gin-pgfc.svg
[gl1]: https://img.shields.io/github/license/apisite/gin-pgfc.svg
[gl2]: LICENSE

<p align="center">
  <a href="../../README.md">English</a> |
  <span>Русский</span>
</p>

* Статус проекта: Реализован концепт

[gin-pgfc] - golang библиотека для использования pgfc в проектах на gin-gonic/

## Использование

```
	allFuncs := template.FuncMap{}
	appendFuncs(allFuncs)

	s, err := pgfc.NewServer(cfg.PGFC, log, cfg.DBConnect, nil)
	if err != nil {
		log.Fatal(err)
	}
	s.SetFuncBlank(allFuncs)
	err = templates.LoadTemplates(allFuncs)
	if err != nil {
		log.Fatal(err)
	}

	s.Route("/rpc", r)

	templates.FuncHandler = func(ctx *gin.Context, funcs template.FuncMap) {
		s.SetFuncRequest(funcs, ctx)
	}

	srv := &http.Server{
		Addr:    cfg.Addr,
		Handler: r,
	}

```
## См. также

* pgfc - golang библиотека для вызова хранимых функций postgresql
* enfist - пример готового приложения

## Лицензия

Лицензия MIT (MIT), см. [LICENSE](LICENSE) (неофициальный перевод,
 [источник перевода](https://ru.wikipedia.org/wiki/%D0%9B%D0%B8%D1%86%D0%B5%D0%BD%D0%B7%D0%B8%D1%8F_MIT), [оригинал лицензии](../../LICENSE)).

Copyright (c) 2018 Алексей Коврижкин <lekovr+apisite@gmail.com>
