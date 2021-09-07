These instructions show how to build Tesseract for Windows using a build standard based on the _GNU autotools_. Other methods use _cmake_ with either the _GNU compiler_ or _Microsoft Visual Studio_. Those other methods are not covered here.

# Cross building from Debian GNU Linux

Cross building means that we compile on Linux, but the resulting programs will run on Windows.
This is our preferred way to build Tesseract for Windows because it is much faster than a native build on Windows.
The instructions here are for Debian GNU Linux, but also work for other Debian based Linux distributions like for example Ubuntu. Other Linux distributions need more or less modifications of these instructions.

## Preconditions

Several packages are needed to allow builds with the _GNU autotools_ and _GNU compilers_. Let's make sure that we have installed them:

    apt install automake build-essentials

In addition, we need the cross tools for building Windows programs:

    apt install mingw-w64 mingw-w64-tools

Finally, several pre-compiled libraries for Windows are needed.
Those libraries are not part of Debian GNU Linux, so we use Cygwin packages which were converted to Debian packages.
TODO.

    for p in mingw64-i686-giflib mingw64-i686-jbigkit mingw64-i686-libjpeg-turbo \
             mingw64-i686-libpng mingw64-i686-libwebp mingw64-i686-openjpeg2 \
             mingw64-i686-tiff mingw64-i686-xz mingw64-i686-zlib; do
        dpkg -i ${p}_*.deb
    done

## Get and build Leptonica

    cd $HOME
    mkdir -p src/github/DanBloomberg
    cd src/github/DanBloomberg
    git clone https://github.com/DanBloomberg/leptonica.git
    cd leptonica
    ./autobuild
    mkdir -p bin/ndebug/i686-w64-mingw32
    cd bin/ndebug/i686-w64-mingw32
    ../../../configure  --host=i686-w64-mingw32 --prefix=/usr/i686-w64-mingw32 CFLAGS='-Wall -Wextra -pedantic -g -O2'
    make
    sudo make install

## Get and build Tesseract

Install Leptonica first.

Finally, several pre-compiled libraries for Windows are needed.
Those libraries are not part of Debian GNU Linux, so we use Cygwin packages which were converted to Debian packages.

    dpkg -i mingw64-i686-bzip2_1.0.6-4_all.deb mingw64-i686-cairo_1.14.12-1_all.deb \
            mingw64-i686-expat_2.2.2-1_all.deb mingw64-i686-fontconfig_2.12.6-1_all.deb \
            mingw64-i686-freetype2_2.6.5-1_all.deb mingw64-i686-gettext_0.19.8.1-2_all.deb \
            mingw64-i686-glib2.0_2.54.3-1_all.deb mingw64-i686-harfbuzz_1.7.4-1_all.deb \
            mingw64-i686-icu_57.1-2_all.deb \
            mingw64-i686-libffi_3.2.1-1_all.deb mingw64-i686-lzo2_2.08-1_all.deb \
            mingw64-i686-pango1.0_1.40.14-1_all.deb mingw64-i686-pcre_8.40-3_all.deb \
            mingw64-i686-pixman_0.34.0-1_all.deb mingw64-i686-win-iconv_0.0.6-2_all.deb

TODO.