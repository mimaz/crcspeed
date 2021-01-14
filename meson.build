project('crcspeed', 'c')

add_project_arguments('-pedantic', language: 'c')

lib = both_libraries(meson.project_name(),
  'crc16speed.c',
  'crc64speed.c',
  'crcspeed.c',
  install: true)

dep = declare_dependency(link_with: lib,
  include_directories: '.')

dep_static = declare_dependency(link_with: lib.get_static_lib(),
  include_directories: '.')

install_headers(
  'crc16speed.h',
  'crc64speed.h',
  'crcspeed.h',
  subdir: 'crcspeed')

if get_option('test')
  executable(meson.project_name(),
    'main.c',
    dependencies: dep,
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
endif

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

meson.override_dependency('crcspeed', dep)
meson.override_dependency('crcspeed-static', dep_static)
