<p align="center">
  <img alt="NETReactorSlayer Logo" src="./Images/Logo-Dark.png#gh-dark-mode-only" width="1000" />
   <img alt="NETReactorSlayer Logo" src="./Images/Logo-Light.png#gh-light-mode-only" width="1000" />
</p>

# .NETReactorSlayer <br /> <a href="https://github.com/SychicBoy/NETReactorSlayer/actions"> <img src="https://github.com/SychicBoy/NETReactorSlayer/actions/workflows/build.yml/badge.svg"></img> <a href="https://github.com/SychicBoy/NETReactorSlayer/actions"> <img src="https://github.com/SychicBoy/NETReactorSlayer/actions/workflows/codeql-analysis.yml/badge.svg"></img> </a> </a> <a href="https://github.com/SychicBoy/NETReactorSlayer/releases/latest"> <img src="https://img.shields.io/github/v/release/SychicBoy/NETReactorSlayer"></img> </a> <a href="#"> <img src="https://img.shields.io/github/downloads/SychicBoy/NETReactorSlayer/total"></img> </a> <a href="#license"> <img src="https://img.shields.io/github/license/SychicBoy/NETReactorSlayer"></img> </a> <a href="https://github.com/SychicBoy/NETReactorSlayer/commits/master"> <img src="https://img.shields.io/github/last-commit/SychicBoy/NETReactorSlayer"></img> </a>

NETReactorSlayer is an open source (GPLv3) deobfuscator and unpacker for [Eziriz .NET Reactor](https://www.eziriz.com/reactor_download.htm).
<br /><br />
<h2 align="center">Preview</h2>

GUI             |  CLI
:-------------------------:|:-------------------------:
<img src="https://user-images.githubusercontent.com/53654076/194274327-cafb86fd-05f3-4320-9c55-83980665ada4.png" width="700">  |  <img src="https://user-images.githubusercontent.com/53654076/194274522-c8fa222d-624c-44c1-954e-6d7659259167.png" width="700">

<br />

### Binaries:
Get the latest stable version from [GitHub releases](https://github.com/SychicBoy/NETReactorSlayer/releases/latest).

### Documentation:
Check out the [Wiki](https://github.com/SychicBoy/NETReactorSlayer/wiki) for guides and information on how to use it.

### Contribution:
Want to contribute to this project? Feel free to open a [pull request](https://github.com/SychicBoy/NETReactorSlayer/pulls).

### Donation:
<a href="https://codestrikers.sellix.io/"> <img src="https://user-images.githubusercontent.com/53654076/192194815-94455dd4-5a6d-4764-877e-f51c65da7d8c.png" width="200"></img> </a>

### License:
NETReactorSlayer is licensed under [GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html).

### Credits:
- [dnlib](https://github.com/0xd4d/dnlib)
- [de4dot.blocks](https://github.com/de4dot/de4dot/tree/master/de4dot.blocks)
- [Harmony](https://github.com/pardeike/Harmony)

---

## Сборка в этом репозитории (форк под net8.0)

```bash
dotnet build NETReactorSlayer.sln -c Release
```

Core / CLI / x64.CLI / De4dot — `net8.0`, GUI — `net8.0-windows`. mono и xbuild
не нужны. GUI собирается из Linux, запускается на Windows.

Артефакты CLI:

```bash
dotnet bin/Release/net8.0/NETReactorSlayer.CLI.dll in.exe --no-pause true
```

Флаги требуют значения: `--no-pause true`. Без `true` ключ съедает путь к файлу.
apphost `bin/Release/net8.0/NETReactorSlayer.CLI` тоже работает, но если SDK
не в системном каталоге, нужен `DOTNET_ROOT=$HOME/.dotnet`.

`x64.CLI` — обёртка под Windows, на .NET Core бесполезна (свой `OutputPath`:
`bin/Release/x64/net8.0/`, иначе гонка за `dnlib.dll` при параллельной сборке).

Проверено на Reactor 4.2: `Robur.exe` 16.0.62.12 — 0 ошибок, 713 типов,
6679 читаемых строковых литералов. 6.0–6.9 заявлены upstream, но на файлах
Robur не проверялись — образцов в репозитории нет.
