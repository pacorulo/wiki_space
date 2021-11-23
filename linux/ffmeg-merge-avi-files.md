ffmpeg - ffmpeg video converter

To merge 2 avi files (persona-1.avi with persona-2.avi in the example below) into one single avi file (it takes only seconds!!!!):
```

        $ ffmpeg -i "concat:persona-1.avi|persona-2.avi" -c copy persona.avi
        ffmpeg version 3.4.6-0ubuntu0.18.04.1 Copyright (c) 2000-2019 the FFmpeg developers
          built with gcc 7 (Ubuntu 7.3.0-16ubuntu3)
          configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
          WARNING: library configuration mismatch
          avcodec     configuration: --prefix=/usr --extra-version=0ubuntu0.18.04.1 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared --enable-version3 --disable-doc --disable-programs --enable-libopencore_amrnb --enable-libopencore_amrwb --enable-libtesseract --enable-libvo_amrwbenc
          libavutil      55. 78.100 / 55. 78.100
          libavcodec     57.107.100 / 57.107.100
          libavformat    57. 83.100 / 57. 83.100
          libavdevice    57. 10.100 / 57. 10.100
          libavfilter     6.107.100 /  6.107.100
          libavresample   3.  7.  0 /  3.  7.  0
          libswscale      4.  8.100 /  4.  8.100
          libswresample   2.  9.100 /  2.  9.100
          libpostproc    54.  7.100 / 54.  7.100
        Input #0, avi, from 'concat:persona-1.avi|persona-2.avi':
          Metadata:
            encoder         : VirtualDubMod 1.5.4.1 (build 2178/release)
            IAS1            : Svenska
            IAS2            : English - Director's Comments
          Duration: 00:43:09.26, start: 0.000000, bitrate: 4537 kb/s
            Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 720x544 [SAR 1:1 DAR 45:34], 23.98 fps, 23.98 tbr, 23.98 tbn, 23.98 tbc
            Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, mono, s16p, 68 kb/s
            Stream #0:2: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, mono, s16p, 72 kb/s
        Output #0, avi, to 'persona.avi':
          Metadata:
            IAS2            : English - Director's Comments
            IAS1            : Svenska
            ISFT            : Lavf57.83.100
            Stream #0:0: Video: mpeg4 (Advanced Simple Profile) (XVID / 0x44495658), yuv420p, 720x544 [SAR 1:1 DAR 45:34], q=2-31, 23.98 fps, 23.98 tbr, 23.98 tbn, 23.98 tbc
            Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 48000 Hz, mono, s16p, 68 kb/s
        Stream mapping:
          Stream #0:0 -> #0:0 (copy)
          Stream #0:1 -> #0:1 (copy)
        Press [q] to stop, [?] for help
        frame=118974 fps=11562 q=-1.0 Lsize= 1386317kB time=01:22:42.21 bitrate=2288.6kbits/s speed= 482x      
        video:1335811kB audio:41680kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: 0.640717%
```
