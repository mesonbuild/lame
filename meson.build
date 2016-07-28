project('lame', 'c', version : '3.99.5')

cc = meson.get_compiler('c')
cdata = configuration_data()
check_headers = [
  ['HAVE_ALLOCA_H', 'alloca.h'],
  ['HAVE_DLFCN_H', 'dlfcn.h'],
  ['HAVE_ERRNO_H', 'errno.h'],
  ['HAVE_FCNTL_H', 'fcntl.h'],
  ['HAVE_INTTYPES_H', 'inttypes.h'],
  ['HAVE_LIMITS_H', 'limits.h'],
  ['HAVE_LINUX_SOUNDCARD_H', 'linux/soundcard.h'],
  ['HAVE_MEMORY_H', 'memory.h'],
  ['HAVE_NCURSES_TERMCAP_H', 'ncurses/termcap.h'],
  ['HAVE_STDINT_H', 'stdint.h'],
  ['HAVE_STDLIB_H', 'stdlib.h'],
  ['HAVE_STRINGS_H', 'strings.h'],
  ['HAVE_STRING_H', 'string.h'],
  ['HAVE_SYS_SOUNDCARD_H', 'sys/soundcard.h'],
  ['HAVE_SYS_STAT_H', 'sys/stat.h'],
  ['HAVE_SYS_TIME_H', 'sys/time.h'],
  ['HAVE_SYS_TYPES_H', 'sys/types.h'],
  ['HAVE_TERMCAP_H', 'termcap.h'],
  ['HAVE_UNISTD_H', 'unistd.h'],
  ['HAVE_XMMINTRIN_H', 'xmmintrin.h'],
]

cdata.set('STDC_HEADERS', 1)

foreach h : check_headers
  if cc.has_header(h.get(1))
    cdata.set(h.get(0), 1)
  endif
endforeach

check_functions = [
  ['HAVE_ALLOCA', 'alloca', '#include<alloca.h>'],
# check token HAVE_EFENCE
  ['HAVE_GETTIMEOFDAY', 'gettimeofday', '#include<sys/time.h>'],
# check token HAVE_ICONV
# check token HAVE_IEEE754_FLOAT32_T
# check token HAVE_IEEE754_FLOAT32_T
# check token HAVE_IEEE754_FLOAT64_T
# check token HAVE_IEEE754_FLOAT64_T
# check token HAVE_IEEE854_FLOAT80
# check token HAVE_IEEE854_FLOAT80_T
# check token HAVE_IEEE854_FLOAT80_T
# check token HAVE_LONG_DOUBLE
# check token HAVE_LONG_DOUBLE_WIDER
# check token HAVE_MPGLIB
# check token HAVE_NASM
  ['HAVE_SOCKET', 'socket', '#include<sys/socket.h>'],
  ['HAVE_STRTOL', 'strtol', '#include<stdlib.h>'],
# check token HAVE_TERMCAP
]

# HACK
if cc.has_header('stdint.h')
  cdata.set('HAVE_UINT8_T', true)
  cdata.set('HAVE_UINT16_T', true)
  cdata.set('HAVE_UINT32_T', true)
  cdata.set('HAVE_UINT64_T', true)
  cdata.set('HAVE_INT8_T', true)
  cdata.set('HAVE_INT16_T', true)
  cdata.set('HAVE_INT32_T', true)
  cdata.set('HAVE_INT64_T', true)
endif

foreach f : check_functions
  if cc.has_function(f.get(1), prefix : f.get(2))
    cdata.set(f.get(0), 1)
  endif
endforeach

cdata.set('SIZEOF_DOUBLE', cc.sizeof('double'))
cdata.set('SIZEOF_FLOAT', cc.sizeof('float'))
cdata.set('SIZEOF_INT', cc.sizeof('int'))
cdata.set('SIZEOF_LONG', cc.sizeof('long'))
cdata.set('SIZEOF_LONG_DOUBLE', cc.sizeof('long double'))
cdata.set('SIZEOF_LONG_LONG', cc.sizeof('long long'))
cdata.set('SIZEOF_SHORT', cc.sizeof('short'))
cdata.set('SIZEOF_UNSIGNED_INT', cc.sizeof('unsigned int'))
cdata.set('SIZEOF_UNSIGNED_LONG', cc.sizeof('unsigned long'))
cdata.set('SIZEOF_UNSIGNED_LONG_LONG', cc.sizeof('unsigned long long'))
cdata.set('SIZEOF_UNSIGNED_SHORT', cc.sizeof('unsigned short'))

configure_file(input : 'config.h.meson',
  output : 'config.h',
  configuration : cdata)

common_args = ['-DHAVE_CONFIG_H']
lameinc = include_directories('include', 'libmp3lame')
confinc = include_directories('.')

m_dep = cc.find_library('m', required : false)

subdir('libmp3lame')
subdir('frontend')

lame_dep = declare_dependency(
  include_directories : lameinc,
  link_with : lamelib,
  )
