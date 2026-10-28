# Сборки без Python (crapper, mutator, dryer)

На **целевой машине** Python не нужен, если положить готовые `.exe` (Windows) или собрать бинарник под macOS/Linux локально.

## Где взять готовые файлы

| Инструмент | GitHub Actions | Release |
|------------|----------------|---------|
| [crapper](https://github.com/Noodle-cpp/crapper) | Actions → **standalone-windows** → Artifacts | тег `v*` → `crapper.exe` |
| [mutator](https://github.com/Noodle-cpp/mutator) | то же → `mutator.exe` | то же |
| [dryer](https://github.com/Noodle-cpp/dryer) | то же → `dryer.exe` | то же |

После merge в **Noodle-cpp** можно вручную запустить workflow **standalone-windows** (`workflow_dispatch`) и скачать artifact, не дожидаясь тега.

## Сборка у себя (Windows)

Нужен **Python 3.11+ один раз** на машине сборки:

```powershell
cd D:\tools\ub\crapper
.\scripts\build-standalone.ps1
# dist\crapper.exe

cd ..\dryer
.\scripts\build-standalone.ps1
# dist\dryer.exe

cd ..\mutator
.\scripts\build-standalone.ps1
# dist\mutator.exe  (внутри уже вшит crapper)
```

`mutator` при сборке тянет **crapper** из соседней папки `..\crapper` или из `$env:CRAPPER_ROOT`.

## Как пользоваться на ПК без Python

```powershell
$bin = "D:\tools\bin"   # каталог с exe в PATH
cd D:\dev\Noodle.IntegrationHub

& "$bin\crapper.exe" .
& "$bin\mutator.exe" .\Noodle.IntegrationHub.Application\Sync\SyncOrchestrator.cs
& "$bin\dryer.exe" .\Noodle.IntegrationHub.Application
```

Поведение и флаги — как у `./crapper` / `./mutator` / `./dryer` в README каждого repo.

## Что Python-бинарник **не** заменяет

| Нужно отдельно | Зачем |
|----------------|--------|
| **.NET SDK** / `dotnet test` | покрытие и тесты C# внутри crapper/mutator |
| **Clojure**, **Go**, **Node**, **Rust**, **Python venv проекта** | тесты и coverage для других языков |
| **Java 21+**, **Clojure CLI** | uml-viewer (Quil) |
| **.NET 8** | uml-viewer-dotnet |

Standalone закрывает только **обёртки quality gate на Python** (tree-sitter, обход файлов, запись `.metrics/`).

## Первый запуск и сеть

Парсеры **tree-sitter** при первом анализе языка могут **скачать grammar** (как при обычном `pip install`). Нужен интернет один раз; дальше кэш в профиле пользователя.

## macOS / Linux

Тот же `packaging/*.spec` и PyInstaller на машине с Python 3.11:

```bash
cd crapper && pip install -e ".[dev]" pyinstaller
pyinstaller packaging/crapper.spec --noconfirm
# dist/crapper — бинарник без .exe
```

CI для Linux/macOS пока не настроен — при необходимости добавьте job по аналогии с `standalone-windows.yml`.

---

См. также [POLNY-CIKL-UB.ru.md](../POLNY-CIKL-UB.ru.md) — полный цикл с companion и viewer.
