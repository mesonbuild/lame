lame_sources = [
  'bitstream.c',
  'encoder.c',
  'fft.c',
  'gain_analysis.c',
  'id3tag.c',
  'lame.c',
  'mpglib_interface.c',
  'newmdct.c',
  'presets.c',
  'psymodel.c',
  'quantize.c',
  'quantize_pvt.c',
  'reservoir.c',
  'set_get.c',
  'tables.c',
  'takehiro.c',
  'util.c',
  'vbrquantize.c',
  'VbrTag.c',
  'version.c',
]

vector_sources = ['vector/xmm_quantize_sub.c']

lamelib = library('mp3lame',
  version : '0.0.0',
  lame_sources, vector_sources,
  include_directories : [lameinc, confinc],
  c_args : common_args,
  dependencies : m_dep,
  install : true)
