project('gst-gzdec', 'c', version : '1.0.0', license : 'AGPL')

plugins_install_dir = join_paths(get_option('libdir'), 'gstreamer-1.0')

cc = meson.get_compiler('c')

gst_version = meson.project_version()

api_version = '1.0'

gst_dep = dependency('gstreamer-1.0', version : '>=1.19',
    required : true, fallback : ['gstreamer', 'gst_dep'])
gstbase_dep = dependency('gstreamer-base-1.0', version : '>=1.19',
  fallback : ['gstreamer', 'gst_base_dep'])

plugin_c_args = ['-DHAVE_CONFIG_H']

cdata = configuration_data()
cdata.set_quoted('PACKAGE_VERSION', gst_version)
cdata.set_quoted('PACKAGE', 'gst-gzip-decoder-plugin')
cdata.set_quoted('GST_LICENSE', 'AGPL')
cdata.set_quoted('GST_API_VERSION', api_version)
cdata.set_quoted('GST_PACKAGE_NAME', 'GStreamer GZIP decoder plugin')
cdata.set_quoted('GST_PACKAGE_ORIGIN', 'https://github.com/javsanpar/gst-gzdec')
configure_file(output : 'config.h', configuration : cdata)

zlib_dep = dependency('zlib')

# The gzdec Plugin
gstgzdec_sources = [
  'src/gstgzdec.c',
]

gstgzdec = library('gstgzdec',
  gstgzdec_sources,
  c_args: plugin_c_args,
  dependencies : [gst_dep, gstbase_dep, zlib_dep],
  install : true,
  install_dir : plugins_install_dir,
)
