common_sources = [
  'main.c',
  'brhist.c',
  'console.c',
  'get_audio.c',
  'lametime.c',
  'parse.c',
  'timestatus.c'
  ]

lame = executable('lame',
  common_sources, 'lame_main.c',
  include_directories : [lameinc, confinc],
  c_args : common_args,
  link_with : lamelib,
  )

mp3rtp = executable('mp3rpt',
  common_sources, 'mp3rtp.c', 'rtp.c',
  include_directories : [lameinc, confinc],
  c_args : common_args,
  link_with : lamelib,
  )

# Do not build as it requires GTK+.
# If someone wants to add this, feel free.
#mp3x = executable('mp3x',
#  'mp3x.c', 'gtkanal.c', 'gpkplotting.c',
#  include_directories : [lameinc, confinc],
#  c_args : common_args,
#  link_with : lamelib,
#  )
