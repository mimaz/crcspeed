project('crcspeed', 'c')

add_project_arguments('-pedantic', language: 'c')

lib = both_libraries(meson.project_name(),
  'crc16speed.c',
  'crc64speed.c',
  'crcspeed.c',
  install: true)

install_headers(
  'crc16speed.h',
  'crc64speed.h',
  'crcspeed.h',
  subdir: 'crcspeed')

executable(meson.project_name(),
  'main.c',
  link_with: lib,
  install: false)

executable('crc64speed-test',
  'crcspeed.c',
  'crc64speed.c',
  c_args: '-DREDIS_TEST_MAIN',
  install: false)

executable('crc16speed-test',
  'crcspeed.c',
  'crc16speed.c',
  c_args: '-DREDIS_TEST_MAIN',
  install: false)

pkg = import('pkgconfig')

pkg.generate(lib,
  subdirs: 'crcspeed',
  version: meson.project_version(),
  name: 'crcspeed',
  description: 'crcspeed library')

pkg.generate(lib.get_static_lib(),
  subdirs: 'crcspeed',
  version: meson.project_version(),
  name: 'crcspeed-static',
  description: 'crcspeed library (static)')
