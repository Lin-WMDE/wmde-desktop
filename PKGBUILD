# Maintainer: WMDE <https://wmde.fun>
# Metapackage: pulls the whole WMDE environment in one `pacman -S wmde-desktop`.
# Grows as components land: wmde-files, wmde-config, inter-font.
pkgname=wmde-desktop
pkgver=1.5.0
# Bumped for the font dependencies below. This metapackage has a STATIC pkgver - no
# pkgver() function - so pkgrel is the only thing that moves, and a depends-only change
# without it ships a package pacman considers identical to the installed one. That is
# exactly what happened: the theme defaults left the old packages, the new dependency was
# never seen, and the desktop lost every appearance default it had.
pkgrel=3
pkgdesc="WMDE desktop metapackage: installs the full WMDE environment"
arch=('any')
url="https://wmde.fun"
license=('GPL-3.0-only')
# qt6ct: Qt6 and KDE applications pick up the WMDE palette through it - start-wmde exports
# QT_QPA_PLATFORMTHEME=qt5ct, a plugin key qt6ct also answers to, and wmde-settings-daemon
# writes the palette into ~/.config/qt6ct. Without the plugin nothing reads it.
# wmde-sysinfo was absorbed by wmde-settings (Hardware sub-page); wmde-settings
# replaces it, so pacman removes the old package on upgrade.
# wmde-themes is mandatory, not cosmetic: it carries every default that decides how the
# desktop looks. Without it the stack falls back to the values compiled into libcosmic,
# which are upstream COSMIC's and drift on every merge.
# The four font packages cover the fallback list hardcoded in cosmic-text
# (src/font/fallback/unix.rs): noto-fonts gives Noto Sans, Noto Sans Mono and Noto Sans
# Symbols, noto-fonts-emoji gives Noto Color Emoji, ttf-dejavu gives DejaVu Sans and DejaVu
# Sans Mono, gnu-free-fonts gives FreeSans and FreeMono. They are mandatory, not cosmetic:
# a family that is missing does NOT degrade to a missing glyph, it makes cosmic-text walk
# the ENTIRE font database, uncached, once per character. Measured on a VM where six of the
# nine families did not resolve: 11607 such walks in one wmde-files run, 12 s of CPU and
# 155 MB of RSS on top of a 45 MB baseline.
depends=('wmde-session' 'wmde-files' 'wmde-term' 'wmde-settings' 'wmde-themes' 'qt6ct'
         'noto-fonts' 'noto-fonts-emoji' 'ttf-dejavu' 'gnu-free-fonts')
# TODO (as they land): 'wmde-config' 'inter-font'

package() {
  :
}
