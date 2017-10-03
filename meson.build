project('zlib', 'c', version : '1.2.11', license : 'zlib')

src = ['adler32.c', 'crc32.c', 'deflate.c', 'infback.c', 'inffast.c', 'inflate.c',
'inftrees.c', 'trees.c', 'zutil.c',
'compress.c', 'uncompr.c', 'gzclose.c', 'gzlib.c', 'gzread.c', 'gzwrite.c']

zlib = library('z', src,
  c_args : ['-DZLIB_DLL'],
  version : meson.project_version(),
  install : true)

install_headers('zlib.h', 'zconf.h')

# pkg-config file
prefixdir = join_paths (get_option('prefix'))
libdir = join_paths(get_option('prefix'), get_option('libdir'))
includedir = join_paths(get_option('prefix'), 'include')
pkgconfigdir = join_paths(libdir, 'pkgconfig')
zlib_pc_conf = configuration_data()
zlib_pc_conf.set('prefix', prefixdir)
zlib_pc_conf.set('exec_prefix', prefixdir)
zlib_pc_conf.set('libdir', libdir)
zlib_pc_conf.set('sharedlibdir', libdir)
zlib_pc_conf.set('includedir', includedir)
zlib_pc_conf.set('PACKAGE_VERSION', meson.project_version())
configure_file(input : 'zlib.pc.in', output : 'zlib.pc',
  configuration : zlib_pc_conf,
  install_dir : pkgconfigdir)

incdir = include_directories('.')

zlib_dep = declare_dependency(link_with : zlib,
  include_directories : incdir)
