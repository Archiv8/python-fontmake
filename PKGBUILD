#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>

_langname="python"
_relname="fontmake"

pkgname="${_langname}-${_relname}"
pkgver=3.3.0
pkgrel=1
pkgdesc="Compile fonts from sources (UFO, Glyphs) to binary (OpenType, TrueType)"
arch=(
  "any"
)
url="https://github.com/googlefonts/fontmake"
license=(
  "Apache"
)
depends=(
  "python"
  "python-attrs"
  "python-fontmath"
  "python-fonttools"
  # For fonttools[ufo]
  "python-fs"
  "python-glyphslib"
  # For fonttools[lxml] and defcon[lxml]
  "python-lxml"
  "python-ttfautohint-py"
  "python-ufo2ft"
  "python-ufolib2"
  # For fonttools[unicode]
  "python-unicodedata2"
)
checkdepends=(
  "python-compreffor"
  "python-defcon"
  "python-mutatormath"
  "python-pytest"
  "python-skia-pathops"
)
makedepends=(
  "python-build"
  "python-installer"
  "python-setuptools-scm"
  "python-wheel"
)
optdepends=(
  "python-mutatormath"
  "python-skia-pathops"
)
_zipname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_zipname}.zip"
)
sha512sums=(
  "f3da85993e5b739ac26d8be74b7069831dbddc6e7f4bf7c7869672b16964b0aacbafaee5a538f62cc75e98f2bdaf578def09e2bc121ee889b0e9fdf4aa3ef58d"
  )

build() {

  cd "${_zipname}"

  python -m build -wn
}

check() {

  cd "${_zipname}"

  PYTHONPATH=Lib pytest tests
}

package() {

  cd "${_zipname}"

  python -m installer -d "${pkgdir}" dist/*.whl
}
