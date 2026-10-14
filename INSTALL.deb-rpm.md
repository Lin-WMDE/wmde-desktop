# Установка на deb/rpm-дистрибутивах без сборки из сырцов вручную

Метапакет: ставит всё окружение WMDE одной командой. Файлов нет, только зависимости.
Автор собирает пакеты у себя локально, как сейчас `makepkg -si`.

Опорные платформы — Debian stable и Fedora: `.deb` собираем на Debian (встаёт и на Ubuntu/Mint),
`.rpm` — на Fedora (встаёт и на RHEL/openSUSE). Наоборот не гарантируется.

Пакет data-only: компиляции нет, только nFPM. Тулчейн не нужен.

## Собрать

```sh
# зависимости сборки: just + nfpm
cargo install --locked nfpm  # или бинарник с github.com/goreleaser/nfpm/releases

just deb   # -> target/wmde-desktop_*.deb
just rpm   # -> target/wmde-desktop-*.rpm
```

Версия статичная `1.10.0`, как `pkgver` в `PKGBUILD` (там специально нет функции —
двигается только `pkgrel`, иначе pacman сочтёт пакет идентичным).

## Поставить

```sh
# Debian/Ubuntu/Mint
sudo apt install ./target/wmde-desktop_*.deb

# Fedora/RHEL/openSUSE
sudo dnf install ./target/wmde-desktop-*.rpm
```

Компоненты WMDE идут в recommends (их пока нет в репозиториях дистрибутивов).
Когда выйдет единый репозиторий WMDE — переключить в depends, как и везде.
