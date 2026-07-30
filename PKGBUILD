# Maintainer: WMDE <https://wmde.fun>
# Metapackage: pulls the whole WMDE environment in one `pacman -S wmde-desktop`.
# Grows as components land: wmde-files, wmde-config, inter-font.
pkgname=wmde-desktop
pkgver=1.5.0
pkgrel=1
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
depends=('wmde-session' 'wmde-files' 'wmde-term' 'wmde-settings' 'wmde-themes' 'qt6ct')
# TODO (as they land): 'wmde-config' 'inter-font'

package() {
  :
}
