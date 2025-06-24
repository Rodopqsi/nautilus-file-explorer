pkgname=nautilus-file-explorer
pkgver=1.0.0
pkgrel=1
pkgdesc="Explorador de archivos gráfico estilo Nautilus con controles de sistema"
arch=('any')
url="https://github.com/Rodopqsi/nautilus-file-explorer"
license=('GPL3')
depends=(
    'python'
    'python-gobject'
    'gtk3'
    'glib2'
    'gdk-pixbuf2'
    'networkmanager'
    'pulseaudio'
    'pulseaudio-alsa'
)
optdepends=(
    'xorg-xbacklight: Control de brillo con xbacklight'
    'brightnessctl: Control de brillo alternativo'
    'vlc: Reproductor multimedia'
    'gstreamer: Soporte multimedia integrado'
    'gst-plugins-base: Códecs básicos'
    'gst-plugins-good: Códecs adicionales'
    'gst-plugins-bad: Códecs menos comunes'
    'gst-libav: Soporte para formatos adicionales'
)
makedepends=('python-setuptools' 'git')
source=("git+$url.git#tag=v$pkgver"
        "nautilus-file-explorer.desktop")
sha256sums=('SKIP' 'SKIP')

build() {
    cd "$srcdir/$pkgname"
    python setup.py build
}

package() {
    cd "$srcdir/$pkgname"
    python setup.py install --root="$pkgdir" --optimize=1

    # Instalar archivo .desktop
    install -Dm644 "$srcdir/nautilus-file-explorer.desktop" "$pkgdir/usr/share/applications/nautilus-file-explorer.desktop"

    # Instalar icono si existe
    if [ -f "icon.png" ]; then
        install -Dm644 "icon.png" "$pkgdir/usr/share/pixmaps/nautilus-file-explorer.png"
    fi
}