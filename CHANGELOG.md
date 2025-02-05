# Changelog

All notable changes to this project will be documented in this file.

## [0.1.10 - 2022-03-1x]

### Added

- class `HeifCompressionFormat(IntEnum)`. `have_decoder_for_format` and `have_encoder_for_format` functions.
- function `libheif_info` that returns dictionary with version and avalaible (en)(de)coders.
- thumbnails support, see new examples.

### Changed

- OPTIONS["avif"] and OPTIONS["strict"] replaced with `options` function, that returns `PyLibHeifOptions` class with that properties.

### Fixed

## [0.1.9 - 2022-03-10]

### Added

- Linux PyPy 3.7 & 3.8 wheels.
- IMPORTANT! `heif_filetype_*` constants will be deprecated in the future. Use `class HeifFiletype(IntEnum)`.
- IMPORTANT! `heif_brand_*` constants will be deprecated in the future. Use `class HeifBrand(IntEnum)`.
- Added `cfg_options` function, to change config when used not as `opener`. Look at `_options.py` for more info.
- OPTIONS: `strict` and `avif` - look at `reader.is_supported` function description.
- `class HeifErrorCode(IntEnum)` to use in custom exception handler.
- `class HeifColorspace(IntEnum)` instead of `heif_colorspace_*` constants.
- `class HeifChannel(IntEnum)` instead of `heif_channel_*` constants.
- `class HeifChroma(IntEnum)` instead of `heif_chroma_*` constants.
- A few examples how to use.

### Changed

- `register_heif_opener` optionally accepts `**kwargs` as parameter, for overwriting values in config, when used as `opener`.
- `check_heif_magic` marked as deprecated. Use `is_supported` function instead.
- `check_heif` always return `HeifFiletype.NO` when there are less 12 bytes in input.
- Warning(`Unssuported HEIF... trying anyway`) was removed.
- `(Undecoded)HeifFile` and `HeifImageFile` classes was slightly changed(more consistent now). See new description in README.md.
- Many other improvements and optimizations.
- When used as reader, functions `open_heif` and `read_heif` raise `HeifError` exception if file is not valid or broken.

### Fixed

- If `color_profile` is `prof` or `rICC` and data empty, `color_profile` will contain `data`=`None` instead of `color_profile`=`None`.
- `check_heif`, `is_supported`, `open_heif` and `read_heif` now preserves file pointer, if input was file handle.

## [0.1.8 - 2022-03-05]

### Added

- Ability to build from source on alpine with arm 7. Thanks to @aptalca

### Changed

- `HeifFile` `close` method now frees image decoded data.
- Code optimization.

### Fixed

## [0.1.7 - 2022-02-27]

### Added

- Added `manylinux2014_i686` wheels.
- Integration of PEP 517 in progress, added new instructions for building from source.

### Changed

- Making code cleaner, renamed cffi module from `pillow_heif.libheif` to `_pillow_heif_cffi`.
- libaom bumped from 3.2.0 to 3.3.0

### Fixed

- Fixed `AttributeError` when calling `Image.verify`. Thanks @zijian-hu for reporting.

## [0.1.6 - 2022-02-10]

### Added

- Windows binary wheels.
- More tests to `as_opener` module.
- Code coverage.
- Linux binary wheels for Python 3.6(this is last release for Python 3.6).

### Changed

- Using code formatting: black.
- Started changing build algorithms to support PEP 517.
- Speed optimizations and adjustments to `as_opener` module.
- Added `info[icc_profile]` to `HeifImageFile` when use it as `as_opener`.
- Adjustments to `reader` module:
- `pillow_heif.open` is in process of deprecation, still available, but you should use `open_heif` instead.
- `pillow_heif.check` is in process of deprecation, still available, but you should use `check_heif` instead.
- `pillow_heif.read` is in process of deprecation, still available, but you should use `read_heif` instead.

### Fixed

- Apple M1 binary wheels now build on Monterey 12.01 instead of 12.2.
- HeifError exception class now calls `super` to init all values.

## [0.1.5 - 2022-02-01]

### Added

- Apple M1 binary wheels.
- Alpine Linux binary wheels.
- More auto tests before publishing.

### Changed

- Python 3.6 is no longer supported.
- libaom bumped from 2.0.0 to 3.2.0

### Fixed

## [0.1.4 - 2021-11-05]

### Added

- GitHub build Actions now use cache.
- Added `libaom` library to linux build.
- More tests.

### Changed

- Code refactoring, readme update.

### Fixed

- Bug with header check when used as plugin for Pillow with `as_opener` function. Thanks for this to @DimonLavron

## [0.1.3 - 2021-10-25]

### Added

- Python 3.10 wheels.
- New function pillow_heif.open() added.(by @homm, more info: https://github.com/carsales/pyheif/pull/55)

### Changed

- Some speed optimizations.(by @homm)

## [0.1.2 - 2021-09-15]

### Fixed

- Fixed empty color profiles work and for images with no exif.

## [0.1.1 - 2021-09-12]

### Added

### Changed

- First working release.
- libde version=1.0.8
- x265 version=3.5
- libheif version=1.12.0

### Fixed
