# ub

Quality gate и UML viewer для разработки с агентом — **форки-компаньоны** [Noodle-cpp](https://github.com/Noodle-cpp).

[English](README.md) · **[Полный цикл (RU)](POLNY-CIKL-UB.ru.md)** · **[Сборки без Python](docs/STANDALONE.ru.md)**

## Репозитории-компаньоны

| Инструмент | Репозиторий |
|------------|-------------|
| **crapper** — CRAP, сложность, покрытие | [github.com/Noodle-cpp/crapper](https://github.com/Noodle-cpp/crapper) |
| **mutator** — мутационное тестирование | [github.com/Noodle-cpp/mutator](https://github.com/Noodle-cpp/mutator) |
| **dryer** — структурные дубли | [github.com/Noodle-cpp/dryer](https://github.com/Noodle-cpp/dryer) |
| **uml-viewer** — UML (Clojure), IR, почта агента | [github.com/Noodle-cpp/uml-viewer](https://github.com/Noodle-cpp/uml-viewer) |
| **ub-mode** — skill агента (дисциплина качества) | [github.com/Noodle-cpp/ub-mode](https://github.com/Noodle-cpp/ub-mode) |
| **uml-viewer-dotnet** — UML без JVM (Avalonia) | рядом с остальными в рабочей папке; README в каталоге `uml-viewer-dotnet/` после клона workspace |

Происхождение: upstream [unclebob/crapper](https://github.com/unclebob/crapper), [mutator](https://github.com/unclebob/mutator), [dryer](https://github.com/unclebob/dryer), [uml-viewer](https://github.com/unclebob/uml-viewer). Форки Noodle-cpp — для companion-потока и доработок (C#, .NET viewer и т.д.).

## Этот репозиторий

Здесь хранится **инструкция по workspace** (`POLNY-CIKL-UB.ru.md`). Исходники инструментов — в таблице выше; для layout «как в гайде» клонируйте их в одну директорию, например:

```text
ub/                    ← этот repo (гайд)
ub/crapper/            ← git clone Noodle-cpp/crapper
ub/mutator/
ub/dryer/
ub/uml-viewer/
ub/ub-mode/
ub/uml-viewer-dotnet/  ← локальный checkout / будущий remote
```

Подробные шаги — в [POLNY-CIKL-UB.ru.md](POLNY-CIKL-UB.ru.md).
