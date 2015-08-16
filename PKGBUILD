# $Id$
# Maintainer : Ionut Biru <ibiru@archlinux.org>
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>
# Contributor: Paul Mattal <paul@archlinux.org>
# Maintainer (Parabola): Márcio Silva <coadde@lavabit.com>

pkgbase=libav
pkgname=libav-static
pkgflag=-static
pkgver=9
pkgrel=1
pkgdesc='Incompatible fork of ffmpeg'
arch=(
  i686
  x86_64
)
url="http://$pkgbase.org/"
license=(
  GPL
)
depends=(
  alsa-lib
  bzip2
  gsm
  lame
  libpulse
  libtheora
  libva
  libvorbis
  libvpx
  opencore-amr
  openjpeg
  rtmpdump
  schroedinger
  sdl
  speex
  x264
  xvidcore
  zlib
)
makedepends=(
  yasm
  libvdpau
)
source=(
  http://$pkgbase.org/releases/$pkgbase-$pkgver.tar.gz
  avconv$pkgflag
  avplay$pkgflag
  avprobe$pkgflag
  avserver$pkgflag
  ffmpeg-$pkgname
  qt-faststart-$pkgname
)
sha512sums=(
  d402c7d586708e29b92340c4d03d8431fe607f0b88c2762cc95671786cdb9a7221968164b571e11086b53b2169f3a657c6106dc769c04a1a035429d011e72610
  4a98c459df5f5bc5e42580b5f2081509719c057fdf55693b3554006b21adcaa29ee59ac0debfe0486fe1df8b9a937135d99e4ccc2df894a2634dd314eed93114
  afd2eadd0a0522cd3665ccd2b819f06a99cc50e3bdac3a0ef200861664c7084cc5990a3c1a860f2f0cc9f835c33c09cb5c57a25dbab0673eb74ba0f4c980e539
  4e557c9eab6a97a3206df1dd49a516ae7be9490c894ff212cb5286ee097ae606c0b7a650c75278a71e4c91d0325eaee729937e1ae659ce0887c3c20ea8fe6333
  f0fa50711d19babf3f485189fb37b17a87f31849dad9cf6a7324601bdde0856fe47d55a4d82c6839c93f39e970edcbeecfbcb70a8b4e7570250fa4c7bb6975fb
  8101ec9c3e0a945ea89f85f81ace52ce67159661e3440668726a5767ba6250a91533494f1aa8fc30ee97ff9af5d64636d0f0dbcb2da862124d35b6b5ec571f5b
  0133fae31e1df586317deb7235f5e74d22abd007038f82b9df10ea3eea6748945c50a0bbe8f588e8a5d1b7874b3fa2639430e1efa32b0cfe16383a32751d3245
)

build() {
  cd "$srcdir/$pkgbase-$pkgver"

  ./configure \
    --prefix=/opt/$pkgname \
    --enable-libmp3lame \
    --enable-libvorbis \
    --enable-libxvid \
    --enable-libx264 \
    --enable-libvpx \
    --enable-libtheora \
    --enable-libgsm \
    --enable-libspeex \
    --enable-shared \
    --enable-x11grab \
    --enable-libopencore_amrnb \
    --enable-libopencore_amrwb \
    --enable-libschroedinger \
    --enable-libopenjpeg \
    --enable-librtmp \
    --enable-libpulse \
    --enable-gpl \
    --enable-version3 \
    --enable-runtime-cpudetect \
    --disable-debug \
    --enable-static

    #--enable-postproc \

  make
  make tools/qt-faststart
  make doc/av{play,server}.1
}

package() {
  cd "$srcdir/$pkgbase-$pkgver"

  make DESTDIR=$pkgdir install install-man
  install -m755 -d                              $pkgdir/etc/ld.so.conf.d
  install -m755 -d                              $pkgdir/usr/bin
  install -m755 -d                              $pkgdir/usr/share/man/man1
  install -Dm755 tools/qt-faststart             $pkgdir/opt/$pkgname/bin
  ln -s /opt/$pkgname/bin/avconv                $pkgdir/usr/bin/avconv$pkgflag
  ln -s /opt/$pkgname/bin/avplay                $pkgdir/usr/bin/avplay$pkgflag
  ln -s /opt/$pkgname/bin/avprobe               $pkgdir/usr/bin/avprobe$pkgflag
  ln -s /opt/$pkgname/bin/avserver              $pkgdir/usr/bin/avserver$pkgflag
  ln -s /opt/$pkgname/bin/ffmpeg                $pkgdir/usr/bin/ffmpeg-$pkgname
  ln -s /opt/$pkgname/bin/qt-faststart          $pkgdir/usr/bin/qt-faststart-$pkgname
  ln -s /opt/$pkgname/share/man/man1/avconv.1   $pkgdir/usr/share/man/man1/avconv$pkgflag.1
  ln -s /opt/$pkgname/share/man/man1/avplay.1   $pkgdir/usr/share/man/man1/avplay$pkgflag.1
  ln -s /opt/$pkgname/share/man/man1/avprobe.1  $pkgdir/usr/share/man/man1/avprobe$pkgflag.1
  ln -s /opt/$pkgname/share/man/man1/avserver.1 $pkgdir/usr/share/man/man1/avserver$pkgflag.1
  ln -s /opt/$pkgname/share/man/man1/ffmpeg.1   $pkgdir/usr/share/man/man1/ffmpeg-$pkgname.1
  echo /opt/libav-static/lib                  > $pkgdir/etc/ld.so.conf.d/libav-static.conf
}

# vim:set ts=2 sw=2 et:
sha512sums=('4b51c89637f675a6075174e417ccd81aadfc7799bb0c70b9c94df43251604643876423645a5b3ed7b7ecc8b3d18db3888662f3e8e8dbc85f49c319ee29bd7e29'
            '4a98c459df5f5bc5e42580b5f2081509719c057fdf55693b3554006b21adcaa29ee59ac0debfe0486fe1df8b9a937135d99e4ccc2df894a2634dd314eed93114'
            'afd2eadd0a0522cd3665ccd2b819f06a99cc50e3bdac3a0ef200861664c7084cc5990a3c1a860f2f0cc9f835c33c09cb5c57a25dbab0673eb74ba0f4c980e539'
            '4e557c9eab6a97a3206df1dd49a516ae7be9490c894ff212cb5286ee097ae606c0b7a650c75278a71e4c91d0325eaee729937e1ae659ce0887c3c20ea8fe6333'
            'f0fa50711d19babf3f485189fb37b17a87f31849dad9cf6a7324601bdde0856fe47d55a4d82c6839c93f39e970edcbeecfbcb70a8b4e7570250fa4c7bb6975fb'
            '8101ec9c3e0a945ea89f85f81ace52ce67159661e3440668726a5767ba6250a91533494f1aa8fc30ee97ff9af5d64636d0f0dbcb2da862124d35b6b5ec571f5b'
            '0133fae31e1df586317deb7235f5e74d22abd007038f82b9df10ea3eea6748945c50a0bbe8f588e8a5d1b7874b3fa2639430e1efa32b0cfe16383a32751d3245')
