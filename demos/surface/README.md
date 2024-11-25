# RTSP devemo based ExoPlayer and FFMPEG


## 1. RTST server 

```markdown
C:\Run\FFMPEG>C:\Run\FFMPEG\mediamtx_v1.9.3_windows_amd64\mediamtx.exe    C:\Run\FFMPEG\mediamtx_v1
.9.3_windows_amd64\mediamtx.yml
2024/11/22 21:58:13 INF MediaMTX v1.9.3
2024/11/22 21:58:13 INF configuration loaded from C:\Run\FFMPEG\mediamtx_v1.9.3_windows_amd64\media
mtx.yml
2024/11/22 21:58:13 INF [RTSP] listener opened on :8554 (TCP), :8000 (UDP/RTP), :8001 (UDP/RTCP)
2024/11/22 21:58:13 INF [RTMP] listener opened on :1935
2024/11/22 21:58:13 INF [HLS] listener opened on :8888
2024/11/22 21:58:13 INF [WebRTC] listener opened on :8889 (HTTP), :8189 (ICE/UDP)
2024/11/22 21:58:13 INF [SRT] listener opened on :8890 (UDP)

```

## 2. FFMPEG feeds camera video data to RTSP server


```markdown

C:\Run\FFMPEG>ffmpeg -f dshow -i video="Logi C270 HD WebCam" -c:v libx264 -f rtsp rtsp://localhost:8554/mystream
ffmpeg version 4.3 Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 9.3.1 (GCC) 20200621
  configuration: --disable-static --enable-shared --enable-gpl --enable-version3 --enable-sdl2 --en
able-fontconfig --enable-gnutls --enable-iconv --enable-libass --enable-libdav1d --enable-libbluray
 --enable-libfreetype --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --e
nable-libopenjpeg --enable-libopus --enable-libshine --enable-libsnappy --enable-libsoxr --enable-l
ibsrt --enable-libtheora --enable-libtwolame --enable-libvpx --enable-libwavpack --enable-libwebp -
-enable-libx264 --enable-libx265 --enable-libxml2 --enable-libzimg --enable-lzma --enable-zlib --en
able-gmp --enable-libvidstab --enable-libvmaf --enable-libvorbis --enable-libvo-amrwbenc --enable-l
ibmysofa --enable-libspeex --enable-libxvid --enable-libaom --enable-libgsm --disable-w32threads --
enable-libmfx --enable-ffnvcodec --enable-cuda-llvm --enable-cuvid --enable-d3d11va --enable-nvenc
--enable-nvdec --enable-dxva2 --enable-avisynth --enable-libopenmpt --enable-amf
  libavutil      56. 51.100 / 56. 51.100
  libavcodec     58. 91.100 / 58. 91.100
  libavformat    58. 45.100 / 58. 45.100
  libavdevice    58. 10.100 / 58. 10.100
  libavfilter     7. 85.100 /  7. 85.100
  libswscale      5.  7.100 /  5.  7.100
  libswresample   3.  7.100 /  3.  7.100
  libpostproc    55.  7.100 / 55.  7.100
Input #0, dshow, from 'video=Logi C270 HD WebCam':
  Duration: N/A, start: 389173.519000, bitrate: N/A
    Stream #0:0: Video: rawvideo (YUY2 / 0x32595559), yuyv422, 640x480, 30 fps, 30 tbr, 10000k tbn,
 10000k tbc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo (native) -> h264 (libx264))
Press [q] to stop, [?] for help
[libx264 @ 0000023c729dea80] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX FMA3 BMI2 AVX2
[libx264 @ 0000023c729dea80] profile High 4:2:2, level 3.0, 4:2:2, 8-bit
[libx264 @ 0000023c729dea80] 264 - core 160 - H.264/MPEG-4 AVC codec - Copyleft 2003-2020 - http://
www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7
psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11
fast_pskip=1 chroma_qp_offset=-2 threads=15 lookahead_threads=2 sliced_threads=0 nr=0 decimate=1 in
terlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 we
ightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 r
c=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, rtsp, to 'rtsp://localhost:8554/mystream':
  Metadata:
    encoder         : Lavf58.45.100
    Stream #0:0: Video: h264 (libx264), yuv422p, 640x480, q=-1--1, 30 fps, 90k tbn, 30 tbc
    Metadata:
      encoder         : Lavc58.91.100 libx264
    Side data:
      cpb: bitrate max/min/avg: 0/0/0 buffer size: 0 vbv_delay: N/A
More than 1000 frames duplicatedN/A time=00:01:04.73 bitrate=N/A dup=998 drop=0 speed=0.969x
More than 10000 frames duplicated/A time=00:11:06.66 bitrate=N/A dup=9994 drop=0 speed=0.997x
av_interleaved_write_frame(): Immediate exit requesteditrate=N/A dup=15343 drop=0 speed=0.998x
frame=30718 fps= 30 q=29.0 Lsize=N/A time=00:17:01.89 bitrate=N/A dup=15351 drop=0 speed=0.998x

video:39890kB audio:0kB subtitle:0kB other streams:0kB global headers:0kB muxing overhead: unknown
[libx264 @ 0000023c729dea80] frame I:123   Avg QP:19.76  size: 58290
[libx264 @ 0000023c729dea80] frame P:7777  Avg QP:22.69  size:  3589
[libx264 @ 0000023c729dea80] frame B:22818 Avg QP:24.52  size:   255
[libx264 @ 0000023c729dea80] consecutive B-frames:  0.7%  0.7%  0.4% 98.2%
[libx264 @ 0000023c729dea80] mb I  I16..4:  5.9% 47.1% 47.0%
[libx264 @ 0000023c729dea80] mb P  I16..4:  0.1%  0.2%  0.0%  P16..4: 52.2%  4.0%  9.4%  0.0%  0.0%
    skip:34.2%
[libx264 @ 0000023c729dea80] mb B  I16..4:  0.0%  0.0%  0.0%  B16..8: 19.4%  0.0%  0
.0%  direct: 0.6%  skip:79.9%  L0:51.4% L1:48.5% BI: 0.1%
[libx264 @ 0000023c729dea80] mb B  I16..4:  0.0%  0.0%  0.0%  B16..8: 19.4%  0.0%  0.0%  direct: 0.
6%  skip:79.9%  L0:51.4% L1:48.5% BI: 0.1%
[libx264 @ 0000023c729dea80] 8x8 transform intra:48.6% inter:66.6%
[libx264 @ 0000023c729dea80] coded y,uvDC,uvAC intra: 70.3% 78.4% 63.4% inter: 4.4% 15.7% 0.2%
[libx264 @ 0000023c729dea80] i16 v,h,dc,p: 58% 10%  3% 29%
[libx264 @ 0000023c729dea80] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 28% 11% 26%  5%  6%  7%  5%  8%  5%
[libx264 @ 0000023c729dea80] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 30% 17% 10%  6%  7%  7%  7%  9%  8%
[libx264 @ 0000023c729dea80] i8c dc,h,v,p: 52% 17% 25%  6%
[libx264 @ 0000023c729dea80] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0000023c729dea80] ref P L0: 44.4%  3.3% 38.2% 14.0%  0.0%
[libx264 @ 0000023c729dea80] ref B L0: 81.2% 12.4%  6.4%

```

At the same time, RTSP console will show

```
2024/11/23 15:00:44 INF [RTSP] [conn [::1]:59986] opened
2024/11/23 15:00:44 INF [RTSP] [session 4b6ff118] created by [::1]:59986
2024/11/23 15:00:44 INF [RTSP] [session 4b6ff118] is publishing to path 'mystream', 1 track (H264)
2024/11/23 15:01:00 INF [RTSP] [conn 127.0.0.1:59997] opened
2024/11/23 15:01:01 INF [RTSP] [session c3f464f0] created by 127.0.0.1:59997
2024/11/23 15:01:01 INF [RTSP] [session c3f464f0] is reading from path 'mystream', with UDP, 1 track (H264)
``````

## 3. Android Emulator

*Note:* 

**!!  Android emulator will use TCP/8554 for grpc by default!!!**

Change to emulator **-gprc 8555** to avoid conflict!!

```markdown
D:\Develop\Android\Sdk>emulator -avd   Pixel_Tablet_API_34    -verbose   -show-kernel  -accel on -grpc  8555
INFO    | Android emulator version 33.1.24.0 (build_id 11237101) (CL:N/A)
DEBUG   | Current emulator version 33.1.24 is the same as the required version 33.1.24.
......................
DEBUG   | goldfish_events.have-multitouch: false
DEBUG   | Adding boot property: 'net.wifi_mac_prefix' = '5554'
DEBUG   | Not using any http proxy
DEBUG   | Adding boot property: 'qemu.timezone' = 'Asia/Shanghai'
DEBUG   | android_hw_fingerprint_init: fingerprint qemud listen service initialized
INFO    | Using security allow list from: D:\Develop\Android\Sdk\emulator\lib\emulator_access.json
WARNING | *** No gRPC protection active, consider launching with the -grpc-use-jwt flag.***
INFO    | Started GRPC server at [::]:8555, security: Insecure, auth: none

.........
``````


## 4. RTSP play

VLC/Android standard  can view rtsp://localhost:8554/mystream

For Android emulator/X86 (10.0.2.15), vlc/Android visit host:   rtsp://10.0.2.2:8554/mystream

This demo is for Android Automotive. Attach log from RTSP server.


```markdown

2024/11/23 15:01:00 INF [RTSP] [conn 127.0.0.1:59997] opened
2024/11/23 15:01:01 INF [RTSP] [session c3f464f0] created by 127.0.0.1:59997
2024/11/23 15:01:01 INF [RTSP] [session c3f464f0] is reading from path 'mystream', with UDP, 1 trac
k (H264)
2024/11/23 15:01:12 INF [RTSP] [session c3f464f0] destroyed: torn down by 127.0.0.1:59997
2024/11/23 15:01:12 INF [RTSP] [conn 127.0.0.1:59997] closed: EOF
2024/11/23 15:01:12 INF [RTSP] [conn 127.0.0.1:60008] opened
2024/11/23 15:01:12 INF [RTSP] [session aabeb007] created by 127.0.0.1:60008
2024/11/23 15:01:12 INF [RTSP] [session aabeb007] is reading from path 'mystream', with TCP, 1 trac
k (H264)
2024/11/23 15:06:58 INF [RTSP] [session aabeb007] destroyed: torn down by 127.0.0.1:60008
2024/11/23 15:06:58 INF [RTSP] [conn 127.0.0.1:60008] closed: read tcp 127.0.0.1:8554->127.0.0.1:60
008: wsarecv: An established connection was aborted by the software in your host machine.
``````



# ExoPlayer SurfaceControl demo

This app demonstrates how to use the [SurfaceControl][] API to redirect video
output from ExoPlayer between different views or off-screen. `SurfaceControl`
is new in Android 10, so the app requires `minSdkVersion` 29.

The app layout has a grid of `SurfaceViews`. Initially video is output to one
of the views. Tap a `SurfaceView` to move video output to it. You can also tap
the buttons at the top of the activity to move video output off-screen, to a
full-screen `SurfaceView` or to a new activity.

When using `SurfaceControl`, the `MediaCodec` always has the same surface
attached to it, which can be freely 'reparented' to any `SurfaceView` (or
off-screen) without any interruptions to playback. This works better than
calling `MediaCodec.setOutputSurface` to change the output surface of the codec
because `MediaCodec` does not re-render its last frame when that method is
called, and because you can move output off-screen easily (`setOutputSurface`
can't take a `null` surface, so the player has to use a `DummySurface`, which
doesn't handle protected output on all devices).

See the [demos README](../README.md) for instructions on how to build and run
this demo.

[SurfaceControl]: https://developer.android.com/reference/android/view/SurfaceControl
