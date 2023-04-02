GZDEC
=====

GStreamer-1.0 example plugin to decompress gzip streams.

Building from Source
--------------------

First see that you have the required build dependencies:

  * meson
  * gstreamer-1.0
  * zlib

```
meson build
ninja -C build
```

Testing the plugin
------------------

```
GST_PLUGIN_PATH=build/ gst-launch-1.0 filesrc location=/tmp/file.txt.gz ! gzdec ! filesink location="/tmp/file.txt"
```
